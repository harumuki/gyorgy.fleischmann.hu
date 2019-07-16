---
layout:   post
title:    MicroFocus / HPE / HP Service Manager 4 
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [microFocus, hpe, hp, service manager, sm, how to]
---

# Table of contents

## Jóváhagyók átmozgatása Request Model-ről, "Line Item Level" jóváhagyásra

```javascript
// update approvalDef and Model and catalog item and move the ranamed approvals

// fake empty approval just for reference
var x = new SCFile( "requestModel" );
x.doSelect( "name=\"" + "Cable" + "\"" );
//print( x.approvals );

// svcCatalog
var sci = new SCFile( "svcCatalog" );
//sci.doSelect( "name=\"STandO Orion\"" );
sci.doSelect( 'active=true and non.cart=true and type="item" and status="Operational"');

var c=1;
do {
	
	var requestModel=lib.svcCatInterface.getXMLFieldValue( sci.interface_info, "requestModel" );
	
	// requestModel
	var m = new SCFile( "requestModel" );
	m.doSelect( "name=\"" + requestModel + "\"" );
		
	if( m.approvals[0][0] != null && sci.support_item != true  ) {

		print( "#" + c + " Catalog item name: " + sci.name );
		//print( sci.interface_info );
	
		print( "Model name: " + m.name );
		print( "Model original approvals: " + m.approvals );
		
		if ( m.approvals.length() == 0 ) {
		  print( "No approval(s)!" );
		  continue;
		};
		
		var approvals = new SCDatum();
		
		for( var i = 0; i < m.approvals.length(); i++ ) {
			approvals.push( renameApproval( m.approvals[i][0] ) );
		}
		//print( approvals );
		
		m.approvals = x.approvals;
		//print ( "Empty appr: " + m.approvals );
		m.doAction( "save" );
		
		sci.approvals = approvals;
		print ( "New approvals: " + sci.approvals );
		sci.doAction( "save" );

		c++;

	}


} while ( sci.getNext() == RC_SUCCESS );

// rename and approvals with SVC prefix
function renameApproval( name ) {

	var a = new SCFile( "ApprovalDef" );
	var aa = new SCFile( "ApprovalDef" );
	var rc = a.doSelect( "name=\"" + name + "\"" );
	
	a.name = "SVC " + a.name;
	
	if( rc == RC_SUCCESS && aa.doCount( "name=\"" + a.name + "\"" ) == 0 ) {
		print( "ApprovalDef rename: [" + a.name + "]" );
		a.doAction( "save" );
	}
 
 	return a.name;
 
}
```

## Jóváhagyók listázása Request Model-en

```javascript
// fake empty approval just for reference
var x = new SCFile( "requestModel" );
x.doSelect( "name=\"" + "Cable" + "\"" );
//print( x.approvals );

// svcCatalog list
var sci=new SCFile( "svcCatalog" );
sci.doSelect( 'active=true and non.cart=true and type="item" and status="Operational"');
print ( sci.doCount( 'active=true and non.cart=true and type="item" and status="Operational"' ) );

print( "### START" );

var i=1;
do {

	var requestModel=lib.svcCatInterface.getXMLFieldValue( sci.interface_info, "requestModel" );
	
	// requestModel
	var m = new SCFile( "requestModel" );
	var c = m.doCount( "name=\"" + requestModel + "\"" )
	m.doSelect( "name=\"" + requestModel + "\"" );
	
	if( m.approvals[0][0] != null && sci.support_item != true  ) {


	print ( "#"+i+". Catalog item name: " + sci.name + " (" + sci.parent[0] + ") " + m.name + " (" + c + ")" );
	print ( "  Model name: " + m.name + " (" + c + ")" );

	print ( "  Model approval(s): " + m.approvals[0][0] ); 
	i++;
	
	}
  
} while( sci.getNext() == RC_SUCCESS );


print( "### END [" + ( i - 1 ) + "]" );
```