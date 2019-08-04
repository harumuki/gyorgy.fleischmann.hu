---
layout:   post
title:    Micro Focus / HPE / HP Service Manager 5 
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [micro focus, hpe, hp, service manager, sm, how to]
---

# Table of contents

## Tricky Comfill buttons

<center><img class="shadow" src="images/sm/mak.im.assignment_button_01.png" style="width: 30%;"> 
        <img class="shadow" src="images/sm/mak.im.assignment_button_02.png" style="width: 30%;"> 
        <img class="shadow" src="images/sm/mak.im.assignment_button_03.png" style="width: 30%;"></center>
<center><img class="shadow" src="images/sm/mak.im.assignment_button_04.png" style="width: 60%;"></center>
<center><img class="shadow" src="images/sm/mak.im.assignment_button_05.png" style="width: 60%;"></center>
<center><img class="shadow" src="images/sm/mak.im.assignment_button_06.png" style="width: 60%;"></center>
<center><img class="shadow" src="images/sm/mak.im.assignment_button_07.png" style="width: 60%;"></center>
<center><img class="shadow" src="images/sm/mak.im.assignment_button_08.png" style="width: 60%;"></center>

```javascript
// getAssignments( affectedItem ) 201907 _flex
function getAssignments( affectedItem ) {

	vars['$mak.assignment.list'] = new Array();

	if( affectedItem == null ) {
		return;
	}

	var fFile = new SCFile( "assignment", SCFILE_READONLY );
	var query = 'active=true and level>=20 and level<=30 and index("' + affectedItem + '", supported.szakrendszerek ) > 0';
	// var query = 'supported.szakrendszerek="' + vars["$L.file"]["affected.item"] + '"'

	var rc = fFile.doSelect( query );

	while ( rc == RC_SUCCESS) {
		vars['$mak.assignment.list'] = system.functions.insert( vars['$mak.assignment.list'], 0, 1, fFile.name );
		rc = fFile.getNext();
	}

}
```

```javascript
// getAssignees( assignment ) 201907 _flex
function getAssignees( assignment ) {

	vars['$mak.assignee.name.list'] = new Array();

	if( assignment == null ) {
		return;
	}

	var fFile = new SCFile( "assignment", SCFILE_READONLY );
	var query = 'name="' + assignment + '"';
	// var query = 'supported.szakrendszerek="' + vars["$L.file"]["affected.item"] + '"'

	var rc = fFile.doSelect( query );

	if ( rc == RC_SUCCESS) {
		vars['$mak.assignee.name.list'] = fFile.operators;
	}

}
```