---
layout:   post
title:    "Halászcsárda projekt"
author:   flex
category: Lifestyle
comments: false
tags:     [lifestyle]

photoswipe: 'yes'

beforeheaderHTML: '<div class="overridemaxwidthboth" style="margin-top: -14px;"><img class="shadow fade" id="fadeimg1" onload="document.getElementById(''fadeimg1'').style.opacity=''1''" style="" src="http://gaultmillau.hu/system/attachments/16570/medium/bajai-teszta-%C3%B6ntve-IMG_2369.jpg?1511647196"></div>'
---
<!--
header_spacer: 93

<div class="shadow" style="position: absolute; left: 0px; top: 0px; width: 100%; z-index: -1; background-image: url(http://gaultmillau.hu/system/attachments/16570/medium/bajai-teszta-%C3%B6ntve-IMG_2369.jpg?1511647196); height: 100%; background-position: center; background-repeat: no-repeat; background-size: cover;"></div>
-->
<!-- http://gaultmillau.hu/buvos-szakacs/halaszle-hagyomanyosan-es-maskepp -->

**2018**(~2017) legérdekesebb projektje, hogy megtaláljuk magyarország legjobb halászcsárdáját a 6-os út környékén. Az első látogatásunk Dunakömlődön volt 2017. november 29-én.

<div id="map-wrap" class="" style="margin-bottom: .75em; -webkit-box-shadow: 0px 4px 18px rgba(0,0,0,0.84); -moz-box-shadow: 0px 4px 18px rgba(0,0,0,0.84); box-shadow: 0px 4px 18px rgba(0,0,0,0.84);">
	<div id="map" style="width:auto; height:100vh;"></div>
</div>

## A birálóbizottság tagjai:

- Dósa István, doffy
- Szabó Miklós, szmiki
- Fleischmann György, _flex

- Polik György, pogyö
- Batári Gábor

## Eddig meglátogatott halászcsárdák:

- Dunakömlődi Halászcsárda, 3x
- Baracsi Halászcsárda, 3x
- Dunaújvárosi Halászcsárda, 1x
- Kigyósi Halászcsárda, 1x
- Római Platán Étterem
- Százhalombattai Halászcsárda

<!-- PhotoSwipeGenerator.pl --directory photos/halaszcsarda_projekt/ --filetag _halaszcsarda_projekt --outdir _includes --imgproperty 'class="shadow zoomeffect"' --title 'Halászcsárda Projekt' -->

{% include photorows.html TAG="halaszcsarda_projekt" %}

## Tervben lévő halászcsárdák:

- Dunaföldvári Halászcsárda
- Tassi halászcsárda

- Szegedi Halászcsárda, Budapest
- Bajai Halászcsárda, Budapest
- Öreghalász Vendéglátó és Kereskedelmi Kft., Budapest
- Új Sipos Halászkert

- Szentendrei határcsárda

- Szúnyog-szigeti Halászcsárda

## Fakultatív csárdalátogatások:

- Révkapu vendéglő, Mohács, >5x
- Peppinó pizzéria, Mohács, >3x
- Alibi bistro, Mohács, 1x
- Kovács Csárda (KOVAČ Čarda), Csúza (Suza)
- Öreg Körössy Halászcsárda, Szeged 

# TOP 3

1. Baracsi Halászcsárda
2. Százhalombattai Halászcsárda
3. ?

<script type='text/javascript' src='https://maps.googleapis.com/maps/api/js?key=AIzaSyAubcKvynd2lNrvNQHlTt6b7Q8OBxDzNOg'></script>

<script type="text/javascript">
	// https://stackoverflow.com/questions/8248077/google-maps-v3-standard-icon-shadow-names-equiv-of-g-default-icon-in-v2
	// https://www.iconfinder.com/icons/248444/church_icon
	var restaurant_icon = 'https://maps.gstatic.com/mapfiles/ms2/micons/restaurant.png';
	var green_pin = 'https://maps.gstatic.com/mapfiles/ms2/micons/grn-pushpin.png';

	var locations = [
		[ 'Dunakömlődi halászcsárda',  		46.6595309, 18.8807809, restaurant_icon ],
		[ 'Baracsi Halászcsárda',      		46.8638776, 18.9175345, restaurant_icon ],
		[ 'Dunaújvárosi Halászcsárda', 		46.9815256, 18.9452692, restaurant_icon ],
		[ 'Kigyósi Halászcsárda',      		46.8065956, 19.1578603, restaurant_icon ],
		[ 'Római Platán Étterem',      		47.5694432, 19.0647115, restaurant_icon ],
		[ 'Százhalombattai Halászcsárda',	47.3105679, 18.9268598, restaurant_icon ],

		[ 'Révkapu vendéglő',          		45.9929783, 18.6942238 ],
		[ 'Peppinó pizzéria',		   		45.9903284, 18.6862382 ],
		[ 'Alibi bistro',              		45.991193,  18.69233 ],
		[ 'Kovács Csárda',             		45.789507,  18.7883592 ],
		[ 'Öreg Körössy Halászcsárda', 		46.2558134, 20.1823772 ],

		[ 'Öreghalász', 					47.5610915, 19.0813481, green_pin ],
	];

	if ( typeof google === 'object' && typeof google.maps === 'object' ) {
		var map = new google.maps.Map( document.getElementById( 'map' ), {
			zoom     : 7.7,
			center   : new google.maps.LatLng( 47.17128, 19.50108 ),
			//mapTypeId: google.maps.MapTypeId.SATELLITE
		} );

		var infowindow = new google.maps.InfoWindow();

		var marker, i;

		for ( i = 0; i < locations.length; i++ ) {
			marker = new google.maps.Marker( {
				position: new google.maps.LatLng( locations[i][1], locations[i][2] ), 
				map: map, 
				icon: locations[i][3]
			} );

			google.maps.event.addListener( marker, 'click', ( function( marker, i ) {
				return function() {
					infowindow.setContent( locations[i][0] );
					infowindow.open( map, marker );
				}
			}) ( marker, i ) );
		}
	}
</script>