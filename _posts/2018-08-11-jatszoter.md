---
layout:   post
title:    Játszótér 2018-
author:   flex
comments: true
category: Personal / személyes
tags:     [én, mi, élet]

photoswipe: 'yes'
---

Ez a [Tátrafüred téri játszótér](https://www.google.hu/maps/place/T%C3%A1traf%C3%BCred+t%C3%A9ri+j%C3%A1tsz%C3%B3t%C3%A9r/@47.4373312,19.2102836,65m/data=!3m1!1e3!4m12!1m6!3m5!1s0x4741c22693021373:0x1f5bd39629f00e01!2zRG9uIEJvc2NvIEvDtnrDtnNzw6lnaSBIw6F6!8m2!3d47.4377019!4d19.2106399!3m4!1s0x4741c22133f57f6d:0x72904f8df77e9ba2!8m2!3d47.4373148!4d19.2104725) lesz az a játszótér, ahova [Andrissal](https://andras.fleischmann.hu/) fogunk járni. 

<!-- break -->

<iframe style="margin-bottom: 0.7em;" width="100%" height="20" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/209935648&&amp;color=ff5500&amp;inverse=false&amp;auto_play=false&amp;show_user=true"></iframe>

<div id="map-wrap" class="" style="margin-bottom: .75em; -webkit-box-shadow: 0px 4px 18px rgba(0,0,0,0.84); -moz-box-shadow: 0px 4px 18px rgba(0,0,0,0.84); box-shadow: 0px 4px 18px rgba(0,0,0,0.84);">
	<div id="map" style="width:auto; height:400px;"></div>
</div>

Meg vagyunk / leszünk mi ezzel rendesen áldva, mert maga a játszótér a [Don Bosco Közösségi ház - Szent István Király Plébánia](http://www.szemere.plebania.hu/don-bosco-kozossegi-haz/) közelében van, sőt itt van még a [Szemeretelepi Református Egyházközség temploma](http://www.refszemeretelep.hu/) és a [Református Egyházmegyék](http://www.reformatus.hu/), jelentsenek ezek pontosan bármit ebben az egyre modernebb világban és a még az új [Coptic Budapest - Szentséges Szűz Mária és Mihály Arkangyal Templom](http://kopttemplom.wixsite.com/kopt) is.

Így néz ki ma (2018.08.12., vasárnap) maga a játszó és néhány környékbeli tereptárgy:

<!-- ../andras.fleischmann.hu/PhotoSwipeGenerator.pl --directory photos/jatszoter2018 --filetag _jatszoter2018 --outdir _includes --title "Tátrafüred téri játszótér 2018" --imgproperty 'class="shadow zoomeffect"' -v -->

{% include photorows.html TAG="jatszoter2018" %}

<script type='text/javascript' src='https://maps.googleapis.com/maps/api/js?key=AIzaSyAubcKvynd2lNrvNQHlTt6b7Q8OBxDzNOg'></script>

<script type="text/javascript">
						var locations = [
							[ 'Játszótér 2018-', 47.4373312, 19.2102836 ],
						];

						if ( typeof google === 'object' && typeof google.maps === 'object' ) {
							var map = new google.maps.Map( document.getElementById( 'map' ), {
								zoom     : 18,
								center   : new google.maps.LatLng( 47.4373312, 19.2102836 ),
								mapTypeId: google.maps.MapTypeId.SATELLITE
							} );

							var infowindow = new google.maps.InfoWindow();

							var marker, i;

							for ( i = 0; i < locations.length; i++ ) {
								marker = new google.maps.Marker( {
									position: new google.maps.LatLng( locations[i][1], locations[i][2] ), map: map
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