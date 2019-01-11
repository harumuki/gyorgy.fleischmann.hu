---
layout:   post
title:    MicroFocus / HPE / HP Service Manager 2 
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [microFocus, hpe, hp, service manager, sm, how to]
---

# Table of contents



Fussunk neki 2!

## Nyelv detektálása

```
sysinfo.get("languagecode")
```

## Porecess Designer 2

### Jóváhagyások (JavaScript)

jscall("GIRO_utils.getManager", deliverer in $L.file)
jscall("GIRO_utils.getManagers", asset.contact.name in $L.file)

```javascript
// Get managers of contacts
// Called by ApprovalDef: Eszközkezelési jóváhagyás
function getManagers( contacts ) {
	var rc;
	var query;
	var fContacts = new SCFile( "contacts", SCFILE_READONLY );
	var aManagers = new Array();
	var i;
	if( contacts != null ) {
		for( i = 0; i < contacts.length(); i++ ) {
			query = "contact.name=\"" + contacts[ i ] + "\"";
			rc = fContacts.doSelect( query );
			if( rc == RC_SUCCESS ) {
				aManagers.push( fContacts.manager );
			}
		}
	}
	return aManagers;
}

// Get manager of contact
// Called by ApprovalDef: Eszközkezelési jóváhagyás
function getManager( contact ) {
	var rc;
	var query;
	var fContacts = new SCFile( "contacts", SCFILE_READONLY );
	query = "contact.name=\"" + contact + "\"";
	rc = fContacts.doSelect( query );
	if( rc == RC_SUCCESS ) {
		return fContacts.manager;
	}
	else {
		return null;
	}
}
```

## Még nem jóváhagyott jóváhagyások összeszedése v1

```javascript
function giroPendingApprovalsNotification ( ) {

	const _MS_PER_DAY = ( 1000 * 60 * 60 * 24 );	
	const _OLDER_DAY = 1;

	var rc;
	
	var fApproval = new SCFile( "Approval", SCFILE_READONLY );

	var query = 'file.name="cm3r" and \
	 			 approval.status="pending" and \
	 			 ( sysmodtime < tod() - \'1 00:00:00\' ) and \
	 			 name="Eszközkezelési jóváhagyás"';

	rc = fApproval.doCount( query );
print("FLEXDEBUG: giroPendingApprovalsNotification Found: [" + rc + "]" );

	rc = fApproval.doSelect( query );
	if ( rc == RC_SUCCESS ) {
    	do {
			//print( fApproval.sysmodtime + ( ( new Date() - fApproval.sysmodtime ) / _MS_PER_DAY > _OLDER_DAY ) + " x " + fApproval.unique_key + " x " + fApproval.current_pending_groups[0] + fApproval.name );
			print( fApproval.sysmodtime + " x " + fApproval.unique_key + " x " + fApproval.current_pending_groups[0] + " -> " + findEmailAddress( fApproval.current_pending_groups[0] ) + " x " + fApproval.name );
		} while ( fApproval.getNext() == RC_SUCCESS )
   	}
}
giroPendingApprovalsNotification ( );
```

```javascript
// Daily notification on pending approvals
function giroPendingApprovalsNotification( ) {

	var rc; 
	var fApproval = new SCFile( "Approval", SCFILE_READONLY );
	var operators = new Array();
	var tickets = new Array();
	//var tod = system.functions.tod();
	//var midnight = system.functions.date(system.functions.tod());

	//var query = 'file.name="cm3r" and approval.status="pending" and sysmodtime<date(tod()) and name="Eszközkezelési jóváhagyás"';
	var query = 'file.name="cm3r" and approval.status="pending" and sysmodtime<tod() and name="Eszközkezelési jóváhagyás"';
	

	rc = fApproval.doSelect( query );
	if ( rc == RC_SUCCESS ) {
    	do {
    	//print(fApproval);
    		var lng = fApproval.current_pending_groups.length();
    		for (var i=0; i<lng; i++) {
    			//print(fApproval.current_pending_groups[ i ]);
    			var idx = lib.ArrayUtil.indexOf( operators, fApproval.current_pending_groups[ i ] );
    			if ( idx < 0 ) {
    				operators.push( fApproval.current_pending_groups[ i ] );
    				tickets.push( fApproval.unique_key );
    			} else {
    				tickets[ idx ] += ", " + fApproval.unique_key;
    			}
    		}
		} while ( fApproval.getNext() == RC_SUCCESS )

		for ( i=0; i<operators.length; i++ ) {
			vars.$G_giro_approval_operator = operators[ i ];
			vars.$G_giro_approval_tickets = tickets[ i ];
			//sendEmailFromHtmlTemplate( fApproval, "GIRO.daily.approval.notification", getOperatorEmail( operators[ i ] ) );
			sendNotification( "GIRO Pending Approval", fApproval, vars.$G_giro_approval_operator );
		}
		
		vars.$G_giro_approval_operator = null;
		vars.$G_giro_approval_tickets = null;
   	}
}

// Returns the email address of the given operator
function getOperatorEmail( name ) {
 
       var fOperator = new SCFile( "operator", SCFILE_READONLY );
       var query = 'name="' + name + '"';
 
       if ( fOperator.doSelect( query ) == RC_SUCCESS ) {
              return fOperator.email;
       }
}

/*function getApprovalURL(file)
{
	var file_name = "Approval";
	var record_name = system.functions.scmsg(file_name,"tablename");
	var record_title = record_name+" "+file.number;
	var record_query = "unique.key=\""+file.number+"\" and approval.status=\"pending\"";

	var web_url = lib.urlCreator.getESSURLFromQuery(file_name,record_query,record_title);
	
	return web_url;
}*/

function sendNotification( strNotificationName, Record, Cimzett ) {

	var rteReturnValue = new SCDatum();
	var rteNames = new SCDatum();
	var rteValues = new SCDatum();
	var argNames = new SCDatum();
	var argVals = new SCDatum();
				  	
	rteNames.push("name"); 
	rteNames.push("record");
	rteNames.push("names");
	rteNames.push("second.file");
	rteNames.push("types");
	
	var argVal;
	argNames.setType(8);	//type array
	argVals.setType(8); 	//type array
	
	argNames.push("$L.Cimzett"); 		 
	argVals.push(Cimzett);
	
	rteValues.setType(8);
	rteValues=system.functions.insert(rteValues, 0, 1, strNotificationName);
	rteValues=system.functions.insert(rteValues, 0, 1, Record);
	rteValues=system.functions.insert(rteValues, 0, 1, argVals);
	rteValues=system.functions.insert(rteValues, 0, 1, Record);
	rteValues=system.functions.insert(rteValues, 0, 1, argNames);
	
	system.functions.rtecall("callrad", rteReturnValue, "us.notify", rteNames, rteValues, false); 
}



```

## Email cím

```javascript
function findEmailAddress( id ) {

	var fContacts = new SCFile( "contacts", SCFILE_READONLY );
	var query = 'operator.id="' + id + '"';

	if ( fContacts.doSelect( query ) == RC_SUCCESS ) {
		return fContacts.email;
	}
}
```

## HTML levélküldés

```javascript
function sendEmailFromHtmlTemplate( record, templateName, recipient ) {
	var subject = system.library.htmlemailtemplates.getMailHeader( templateName, record, record, recipient, vars.$L_mailLang );                                                                         
	var emailBody = lib.htmlemailtemplates.getMailBody( templateName, record, record, recipient, vars.$L_mailLang );
	sendEmail( recipient, recipient, subject, emailBody);
}
 
/*
*  send email to per recipient
*
*  @param         {String}   recipient - the recipient of the email
*            @param               {String}   subject - the subject of the email
*            @param               {String}   emailBody -  the email body
*/

function sendEmail( contact, recipient, subject, emailBody ) {
	var email = new SCFile( "mail" );
 
	email["user.to"] = recipient;
	email["user.from"] = system.functions.operator();
	email["date.to.send"] = system.functions.tod();
	email["status"] = "sent";
	email["subject"] = subject;
	email["application"] = "email";
	email["text"].push( emailBody );
	email["user.array"][0] = contact;

	var paramNames = new SCDatum();
	var paramValues = new SCDatum();

	paramNames.push( "record" );
	paramValues.push(email);

	var rteReturnValue = "";
	var rc = system.functions.rtecall( "callrad", rteReturnValue,
                                       "axces.email", //RAD app name
                                       paramNames,
                                       paramValues,
                                       false ); //false to run in same thread, true to run in new thread
 
	return rc;
}
```

## Táblázat validáció v1

```javascript
// Called by RuleSet: GIRO.chm.am.list.table
function tableValidation( change ) {
	
	var i, j;
	var lista = [];
	var text = "";
	
print("FLEXDEBUG: Start on [#" + change.asset_name.length() + "]");	
	
	// Loop through the rows
	for ( i = 0; i < change.asset_name.length(); i++ ) {
	
		var tag = change[ "asset.asset.tag" ][i]
	
		if ( tag != null && tag != tag.match( /^L\d{7}$/ ) ) {
			lista.push("A(z) [" + (i+1) + "] sorban nem megfelelő a sorozatszám formátuma: " + tag + " !" );
		}
	
	}
	
	for ( i = 0; i < lista.length; i++ ) {
		text = text + lista[i] + "\n";
	}
	doMsgBox( text, 3 );
	
print("FLEXDEBUG: End.");		
	
	return 0;
}

// Popup message
function doMsgBox ( message, level ) {
	var rteReturnValue = new SCDatum();
	var argNames = new SCDatum();
	var argVals = new SCDatum();
	argVals.setType(8);     //type array
	argNames.setType(8);    //type array
	var argVal;

	argVal=new SCDatum();
	argVal.setType(2); //string
	argVal="text";
	argNames.push(argVal);

	argVal=new SCDatum();
	argVal.setType( 2 ); //string
	argVal = message;
	argVals.push( argVal );
	
	argVal="index";
	argNames.push(argVal);
	
	argVal = level;
	argVals.push( argVal );

	system.functions.rtecall("callrad",
		rteReturnValue,
		"mb.ok", //RAD app name
		argNames,
		argVals,
		true); //false to run in same thread, true to run in new thread
}
```

## Validációk

```javascript
//GIROassetAssetTagAutocorrectL
function GIROassetAssetTagAutocorrectL( change ) {
	var i, lista = [], messageText = "";

	// loop through the rows and correct the wrong numbers
	for ( i = 0; i < change.asset_name.length(); i++ ) {
		var tag = change[ "asset.asset.tag" ][i]
	 	if ( tag != null && tag.match( /^\d{1,7}$/ ) ) {
	 		change[ "asset.asset.tag" ][i] = "L" + change[ "asset.asset.tag" ][i]
  	   		lista.push( ( i + 1) + ". sorban [" + tag + "] !" );
	 	}
	}
	
	// generate a warning messsage
	if ( lista.length > 0 ) {
		messageText += "A következő sorokban automatikusan javítottuk a leltári számot:\n\n"
		for ( i = 0; i < lista.length; i++ ) {
			messageText += lista[i] + "\n";
		}	
		doMsgBox( messageText, 3 );
	}
	
	return 0;
}

// validate asset.asset.tags filed in table
// Called by RuleSet: GIRO.asset.Asse.TagValidation
function GIROassetAssetTagValidation( change ) {
	var i, lista = [], messageText = "";

	// loop through the rows and collect the wrong numbers
	for ( i = 0; i < change.asset_name.length(); i++ ) {
		var tag = change[ "asset.asset.tag" ][i]
	 	if ( tag != null && !tag.match( /^L\d{7}$/ ) ) {
  	   		lista.push( ( i + 1) + ". sor [" + tag + "] !" );
	 	}
	}
	
	//generate a warning messsage
	if ( lista.length > 0 ) {
		messageText += "A következő sorokban nem megfelelő a leltári szám formátuma:\n\n"
		for ( i = 0; i < lista.length; i++ ) {
			messageText += lista[i] + "\n";
		}	
		messageText += "\nKérem javítsák ki megfelelő formátumra!"
		doMsgBox( messageText, 3 );
		return -1;
	}
	
	return 0;
}
```

## Üzenet küldése a szerver logjába

```javascript
system.functions.rtecall("log", vars.$L_rc, sMessage); 
````

## Kliens IP címe

RAD: d sysinfo.get( "ClientNetAddress" )
JavaScript: print( system.functions.sysinfo_get( "ClientNetAddress" ) );

## Kliens aktuális nyelve

RAD: d sysinfo.get( "LanguageCode" )
JavaScript: print( system.functions.sysinfo_get( "LanguageCode" ) );

##

RAD: d version( )
JavaScript: print( system.functions.version( ) );

## Értesítések

command( db, notification )

command( db, htmltemplates )
