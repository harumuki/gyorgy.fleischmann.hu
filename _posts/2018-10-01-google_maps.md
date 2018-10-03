---
layout:   post
title:    "Google Maps API"
author:   flex
category: HTML
comments: true
tags:     [web, development, fejlesztés, html, css, jekyll, google, google map, map, api, hun]

photoswipe: 'yes'
---

Gyorsan felteszem 1 terképre, hogy én merre jártam eddig a világban:

<script type='text/javascript' src='https://maps.googleapis.com/maps/api/js?key=AIzaSyAubcKvynd2lNrvNQHlTt6b7Q8OBxDzNOg'></script>

<div id="map-wrap" class="overridemaxwidthboth" style="-webkit-box-shadow: 0px 4px 18px rgba(0,0,0,0.84); -moz-box-shadow: 0px 4px 18px rgba(0,0,0,0.84); box-shadow: 0px 4px 18px rgba(0,0,0,0.84); margin-bottom: .5em;">
	<div id="map" style="width:auto; height:650px;"></div>
</div>

Ahhoz, hogy ezt meg tudjam csinálni kell 1 Google Maps API kulcs, amit itt lehet szerezni: [https://console.cloud.google.com/](https://console.cloud.google.com/) és itt 1 kis segítség, hogy pontosan hol lehet ezt megtalálni:

<!-- PhotoSwipeGenerator.pl --filelist images/google_maps/google_maps.lst --filetag _google_maps --outdir _includes --imgproperty 'class="shadow zoomeffect"' --title 'Google API key' -verb -->

{% include photorows.html TAG="google_maps" %}

és utána akár ezzel a linkkel vársonként egyenként: 

```
http://maps.googleapis.com/maps/api/geocode/json?address=Moh%C3%A1cs&sensor=false&key="Insert your own API key"
```

vagy akár R-ben ezekkel a parancsokkal:

<pre class="terminal">
r
> install.packages('ggmap')
> library(ggmap) 
> geocode("Mohács")
</pre>

vagy2 perl-ben ezeknek a perl moduloknak a telepítése után:

<pre class="terminal">
sudo cpan i Mozilla::CA
sudo cpan i Geo::Coder::Google
</pre>

ezzel a rövid kis szkripttel akár egy fájlból olvasva a vársok nevét, le leht gyártani egy tömböt a koordinátákkal. Én ezt használtam:

```perl
#!/usr/bin/perl

# geocode.pl
#
# Designed by _flex
# Written  by _flex from FleXoft.
#   (gyorgy@fleischmann.hu)
#
# v1.00, 2018.10.01. Budapest, FleXoft
#   Rls:  first release
#
# Requirements:
# -------------
#
#	sudo cpan i Mozilla::CA
#	sudo cpan i Geo::Coder::Google
#
# Documentation:
# --------------
#
#	Tested on:
#		This is perl 5, version 18, subversion 2 (v5.18.2) built for darwin-thread-multi-2level
#       Geo::Coder::Google	0.19
#		Geo::Coder::Google::V2	0.19
#		Geo::Coder::Google::V3	0.19  
#
# TODO:
# -----
#

use strict;
use warnings;
use utf8;

print "  ______ _______  _____  _______  _____   ______  _______   _____\n";
print " |  ____ |______ |     | |       |     | |     \  |______   |_____] |\n";
print " |_____| |______ |_____| |_____  |_____| |_____/ |______ . |       |_____\n";
print "\n";

use Geo::Coder::Google;
my $geocoder = Geo::Coder::Google->new( apiver => 3, key => "Insert your own API key", sensor => "false" );

open( FH, "<cities.txt" ) || die "Cannot open file: $!";
while ( <FH> ) {
	chomp;
	next if ( /^(\s)*$/ or /^#.*/ );

	my $city = $_;
	my $location = $geocoder->geocode( location => "$city" );

	print '[ "'."$city".'", '.$location->{geometry}{location}{lat}.", ".$location->{geometry}{location}{lng}." ],\n";
}
```
Github link: [https://github.com/FleXoft/geocode.pl](https://github.com/FleXoft/geocode.pl)

<script type="text/javascript">
						var locations = [

[ "Mohács", 46.0046295, 18.6794304 ],
[ "Lánycsók", 46.0073964, 18.624077 ],
[ "Székelyszabar", 46.0471326, 18.6012321 ],
[ "Babarc", 46.0042229, 18.5527511 ],
[ "Siklós", 45.8555814, 18.2979721 ],
[ "Pécs", 46.0727345, 18.232266 ],
[ "Harkány", 45.8534053, 18.2348372 ],
[ "Dombay tó", 46.1467713, 18.3977164 ],
[ "Kölked", 45.9489796, 18.7058024 ],
[ "Szentgotthár", 46.9500038, 16.2853985 ],
[ "Csörötnek", 46.9498177, 16.3707766 ],
[ "Komló", 46.1929788, 18.2512139 ],
[ "München", 48.1351253, 11.5819805 ],
[ "Friedrichshafen", 47.6617648, 9.4800113 ],
[ "Szeged", 46.2530102, 20.1414253 ],
[ "Kecskemét", 46.8963711, 19.6896861 ],
[ "Szekszárd", 46.3474326, 18.7062293 ],
[ "Paks, Hungary", 46.6060722, 18.8546832 ],
[ "Tamási", 46.6332018, 18.2854998 ],
[ "Győr", 47.6874569, 17.6503974 ],
[ "Eger", 47.9025348, 20.3772284 ],
[ "Aggtelek", 48.5080267, 20.5400313 ],
[ "Debrecen", 47.5316049, 21.6273124 ],
[ "Lilafüred", 48.0985669, 20.621813 ],
[ "Mátra", 47.8833333, 19.95 ],
[ "Dömös", 47.7644099, 18.9104042 ],
[ "Kaposvár", 46.3593606, 17.7967639 ],
[ "Dunaújváros", 46.9619059, 18.9355227 ],
[ "Trencsény", 48.884936, 18.0335208 ],
[ "Párizs", 48.856614, 2.3522219 ],
[ "Barcelóna", 41.3850639, 2.1734035 ],
[ "Madrid", 40.4167754, -3.7037902 ],
[ "Róma", 41.9027835, 12.4963655 ],
[ "Athén", 37.9838096, 23.7275388 ],
[ "London", 51.5073509, -0.1277583 ],
[ "Isztambul", 41.0082376, 28.9783589 ],
[ "Frankfurt", 50.1109221, 8.6821267 ],
[ "Reading, UK", 51.4542645, -0.9781303 ],
[ "Zágráb", 45.8150108, 15.9819189 ],
[ "Belgrád", 44.786568, 20.4489216 ],
[ "Zadar", 44.119371, 15.2313648 ],
[ "Sibenik", 43.7350196, 15.8952045 ],
[ "Split", 43.5081323, 16.4401935 ],
[ "Makarska", 43.2937769, 17.0215239 ],
[ "Vir, Horvátország", 44.3005078, 15.0859668 ],
[ "Velence, Italy", 45.4408474, 12.3155151 ],
[ "Rimini", 44.0678288, 12.5695158 ],
[ "Tunisz", 36.8064948, 10.1815316 ],
[ "Korinthosz", 37.9386365, 22.9322383 ],
[ "Tallin", 59.4369608, 24.7535747 ],
[ "Travemünde, Lübeck, Németország", 53.9600008, 10.8535751 ],
[ "Trelleborg, Schweden", 55.3762427, 13.1574232 ],
[ "Koppenhága", 55.6760968, 12.5683372 ],
[ "Isztambul", 41.0082376, 28.9783589 ],
[ "Prága", 50.0755381, 14.4378005 ],
[ "Ljubljana", 46.0569465, 14.5057515 ],
[ "Bledi tó", 46.363598, 14.0938053 ],
[ "Krakow", 50.0646501, 19.9449799 ],
[ "Reykjavik", 64.146582, -21.9426354 ],
[ "Neszebár", 42.6601365, 27.7205593 ],
[ "Tátra", 49.1556982, 20.0442995 ],
[ "Arad", 46.1865606, 21.3122677 ],
[ "Temesvár", 45.7488716, 21.2086793 ],
[ "Szabadka", 46.1005467, 19.6650593 ],
[ "Budapest ", 47.497912, 19.040235 ],
[ "Bécs", 48.2081743, 16.3738189 ],
[ "Atlanta", 33.7489954, -84.3879824 ],
[ "Memphis", 35.1495343, -90.0489801 ],
[ "Chattanuga", 35.0456297, -85.3096801 ],
[ "Gatlinburg", 35.714259, -83.5101638 ],
[ "Birmingham", 33.5185892, -86.8103567 ],
[ "Rock city mountains", 34.9733918, -85.3501772 ],
[ "New Orleans", 29.9510658, -90.0715323 ],
[ "Lake Pont chartrain", 30.205062, -90.1120696 ],
[ "Dallas", 32.7766642, -96.7969879 ],
[ "Memphis", 35.1495343, -90.0489801 ],
[ "Cincinaty", 39.1031182, -84.5120196 ],
[ "New York", 40.7127753, -74.0059728 ],
[ "Bécs", 48.2081743, 16.3738189 ],
[ "New York", 40.7127753, -74.0059728 ],
[ "Miami", 25.7616798, -80.1917902 ],
[ "Homestead, Florida", 25.4687224, -80.4775569 ],
[ "Everglades", 25.745929, -80.5549561 ],
[ "Keywest", 24.5550593, -81.7799871 ],
[ "Fort Lauderdale", 26.1224386, -80.1373174 ],
[ "Orlando", 28.5383355, -81.3792365 ],
[ "Cape canaveral", 28.4740089, -80.5771737 ],
[ "Miami", 25.7616798, -80.1917902 ],
[ "Boston", 42.3600825, -71.0588801 ],
[ "Capecod", 41.6687897, -70.2962408 ],
[ "Albany", 42.6525793, -73.7562317 ],
[ "Niagara", 43.0828162, -79.0741629 ],
[ "Ittaca", 25.7639806, -80.2594655 ],
[ "Harisburg", 40.2731911, -76.8867008 ],
[ "Lancaster, Pennsylvania", 40.0378755, -76.3055144 ],
[ "Shanon doah", 38.2927558, -78.6795836 ],
[ "Washington, D.C.", 38.9071923, -77.0368707 ],
[ "Philadelphia", 39.9525839, -75.1652215 ],
[ "Savannah", 32.0808989, -81.091203 ],
[ "Machester, NH", 42.9956397, -71.4547891 ],
[ "North Convay, NH", 44.0536805, -71.1284041 ],
[ "Acadia, ME", 44.3385559, -68.2733346 ],
[ "Bar Harbour, ME", 44.3876119, -68.2039123 ],
[ "Saint John, NB", 45.2733153, -66.063308 ],
[ "Halifax, NS", 44.6487635, -63.5752387 ],
[ "Fredericton, NB", 45.9635895, -66.6431151 ],
[ "Quebec City", 46.8138783, -71.2079809 ],
[ "Montreal", 45.5016889, -73.567256 ],
[ "Ottawa", 45.4215296, -75.6971931 ],
[ "Drezda", 51.0504088, 13.7372621 ],

						];

						if ( typeof google === 'object' && typeof google.maps === 'object' ) {
							var map = new google.maps.Map( document.getElementById( 'map' ), {
								zoom     : 2,
								center   : new google.maps.LatLng( 0, 0 ),
								mapTypeId: google.maps.MapTypeId.ROADMAP
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