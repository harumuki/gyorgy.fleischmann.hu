---
layout:   post
title:    Micro Focus / HPE / HP Service Manager 3 
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [micro focus, hpe, hp, service manager, sm, how to]
---

# Table of contents

## Trace lehetőségek

```javascript
$L.void=rtecall( "log", $L.rc, "DEBUG:" + $query )

# javascript
 var rc;
system.functions.rtecall( "log", rc, "DEBUG:" + vars.$query );
```

```javascript
print( "DEBUG: " + vars.$query );
```

SM alkalmazás szintű logolás szeparálása

```javascript
#LB
sm -loadBalancer -httpPort:13080 -log:../logs/lb.log
 
# web
sm -httpPort:13081 -ssl:0 -sslConnector:0 -log:../logs/webclient.log
 
#smclient(GUI)
sm -httpPort:13090 -ssl:0 -sslConnector:0 -log:../logs/windowsclient.log
 
# CIT
sm -httpPort:13089 -debugnode -ssl:0 -sslConnector:0 -log:../logs/CIT.log
```

Egyedi fájlba (Köszi Mozi!)

```javascript
function writeToFile( path, binary, object ) {
 
	print( "Writing to file...> " + path );
 
	var output = writeFile( path, binary, object );
 
	//print( "The number of bytes written to file was: " + output );
 
	return output;
}
 
function writeLocations() {
 
	filePath = "C:\\_unloads/locations.txt"; //Path on Server
	isBinary = null;
 
	var temp_arr = "";
 
	var loc = new SCFile( "location" );
 
	//*******if you want to using a query with date
	//var theXMLDate = new XMLDate(new Date());
	//var todaysDate = theXMLDate.getSCDateTimeString();
	 
	//var query = "sysmodtime>'"+todaysDate+ "' - '2 00:00:00'";
	 
	var query = 'location<>""'
	loc.doSelect( query )
 
	var i=1;
	 
	print( "***START***" );

	do { 
		temp_arr += i + ";" + loc.location + ";" + loc.location_name + ";" + loc.city;
		temp_arr += "\n";
		i++;
	} while ( loc.getNext() == RC_SUCCESS );
  
	fileObject = temp_arr;
	 
	writeToFile( filePath, isBinary, fileObject );

	print( "***END***" );
}
 
writeLocations();
```

## Változók

```javascript
Format Control (FC)
	Validation: null( company in $file ) and not  ( null ( mol.tmp.company in $file ) ) or same( $G.bg, true )
		Calculation: company in $file = nullsub( company in $file, mol.tmp.company in $file ) 
```

```javascript
Triggers (triggers)
if (record.type == "storage" || record.type == "sim" || record.type == "cluster" || record.type == "networkcomponents" || record.type == "officeelectronics" || record.type == "printer" || record.type == "accessory" || record.type == "mobiledevice" || record.type == "computer" || record.type == "displaydevice" || (record.type == "application" && record.subtype == "DSL") ) {

	record.sm_device_display_name = lib.MOL_utils.createDisplayLabel( record );

}

if ((record.company == "" || record.company == null) && record.mol_tmp_company != null) {

	record.company = record.mol_tmp_company;

}
```

## Kereső form kiíratása

d $L.search.format

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