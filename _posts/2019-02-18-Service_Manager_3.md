---
layout:   post
title:    MicroFocus / HPE / HP Service Manager 3 
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [microFocus, hpe, hp, service manager, sm, how to]
---

# Table of contents

## Trace lehetőségek

```javascript
$L.void=rtecall( "log", $L.rc, "DEBUG:" + $query )
```

```javascript
print( "DEBUG: " + vars.$query );
```

## HTML levélküldés 0

```javascript
lib._flex.sendEmailFromHtmlTemplate( vars.$L_file, "_flex SM HTML Notification", "flex" );
```

## HTML levélküldés 1

```javascript
function sendEmailFromHtmlTemplate( record, templateName, recipient ) {
  	sendNotification( templateName, record, getOperatorEmail(recipient) );
}

function sendNotification( strNotificationName, Record, Cimzett ) {

print( strNotificationName )
print ( getOperatorEmail(Cimzett) )

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

// Returns the email address of the given operator
function getOperatorEmail( name ) {
 
       var fOperator = new SCFile( "operator", SCFILE_READONLY );
       var query = 'name="' + name + '"';
 
       if ( fOperator.doSelect( query ) == RC_SUCCESS ) {
              return fOperator.email;
       }
}
```

## HTML levélküldés 2

```javascript
/* Sends html email to recipient */
function sendEmailFromHtmlTemplate( record, templateName, recipient ) {

    var templateName = "_flex_SM_HTML_Template"

	var subject = system.library.htmlemailtemplates.getMailHeader( templateName, record, record, recipient, "en" );	//vars.$L_mailLang				
	var emailBody = lib.htmlemailtemplates.getMailBody( templateName, record, record, recipient, "en" ); //vars.$L_mailLang

	sendEmail( recipient, recipient, subject, emailBody);
}
/**/

/*
 *  send email to per recipient
 *
 *     @param	 {String}   recipient - the recipient of the email
 *	@param	 {String}   subject - the subject of the email
 *	@param	 {String}   emailBody -  the email body
 *
*/

function sendEmail( contact, recipient, subject, emailBody ) {
	var email = new SCFile("mail");

	email["user.to"] = recipient;
	email["user.from"] = system.functions.operator();
	email["date.to.send"] = system.functions.tod();
	email["status"] = "sent";
	email["subject"] = subject;
	email["application"] = "email";
	email["text"].push(emailBody);
	email["user.array"][0] = contact;

	var paramNames = new SCDatum();
	var paramValues = new SCDatum();

	paramNames.push("record");
	paramValues.push(email);

	var rteReturnValue = "";
	var rc = system.functions.rtecall("callrad",
										rteReturnValue,
										"axces.email", //RAD app name
										paramNames,
										paramValues,
										false); //false to run in same thread, true to run in new thread

	return rc;
}
/**/
```

## Értesítések

command( db, notification )

command( db, htmltemplates )