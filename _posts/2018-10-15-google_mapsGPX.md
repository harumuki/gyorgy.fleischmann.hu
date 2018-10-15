---
layout:   post
title:    "Google Maps API GPX"
author:   flex
category: HTML
comments: true
tags:     [web, development, fejlesztés, html, css, jekyll, google, google map, map, api, hun]

photoswipe: 'yes'
---

Teszt 1 GPX:

<script type='text/javascript' src='https://maps.googleapis.com/maps/api/js?key=AIzaSyAubcKvynd2lNrvNQHlTt6b7Q8OBxDzNOg'></script>

<div id="map-wrap" class="overridemaxwidthboth" style="-webkit-box-shadow: 0px 4px 18px rgba(0,0,0,0.84); -moz-box-shadow: 0px 4px 18px rgba(0,0,0,0.84); box-shadow: 0px 4px 18px rgba(0,0,0,0.84); margin-bottom: .5em;">
	<div id="map" style="width:auto; height:650px;"></div>
</div>

<script type="text/javascript"
    src="http://ajax.googleapis.com/ajax/libs/jquery/1.6.1/jquery.min.js">
</script>

<script type="text/javascript"
    src="js/gpxviewer.js">
</script>

<!-- https://github.com/peplin/gpxviewer -->

<script type="text/javascript">

function loadGPXFileIntoGoogleMap( map, filename ) {
	$.ajax( {url: filename,
	    dataType: "xml",
	    success: function( data ) {
	      var parser = new GPXParser( data, map );
	      parser.setTrackColour( "#ff0000" );     	// Set the track line colour
	      parser.setTrackWidth( 5 );          		// Set the track line width
	      parser.setMinTrackPointDelta( 0.001 );	// Set the minimum distance between track points
	      parser.centerAndZoom( data );
	      parser.addTrackpointsToMap();         	// Add the trackpoints
	      parser.addRoutepointsToMap();         	// Add the routepoints
	      parser.addWaypointsToMap();           	// Add the waypoints
	    }
	});
	}

	$(document).ready(function() {
		var infowindow = new google.maps.InfoWindow();

		var map = new google.maps.Map( document.getElementById( 'map' ), {
			zoom     : 3.5,
			center   : new google.maps.LatLng( 50, -33 ),
			mapTypeId: google.maps.MapTypeId.ROADMAP
		} );

	    loadGPXFileIntoGoogleMap( map, "gpx/MOM2HOME20181015.gpx" );
	    //loadGPXFileIntoGoogleMap( map, "gpx/kornati.gpx" );
	});

</script>