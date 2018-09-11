---
layout:   post
title:    Transversion
author:   flex
comments: true
category: Development / fejlesztés
tags:     [pico-8, development, zx spectrum, retro, game]

beforeheaderHTML: '<center><img class="overridemaxwidthboth" style="" src="images/transversion//zx_spectrum.png"></center>'
---

<div class="rightbox" style="width:40%;"><a href="http://www.top80sgames.com/site/content/transversion"><img class="shadow" src="images/transversion/transversion_tape_cover.jpg" alt="Original Transversion tape cover"></a></div>


<span class="initial">V</span>alamikor 1983 környékén vettük (nem tudom már, hogy pontosan milyen körülmémyek között, de az biztos, hogy valahogy feketén érkezett az országba) az első számítógépünket, egy Sinclair ZX Spectrum 48K-s modellt. A gép még az alap, gumi billentyűzetes volt és a kicsomgaolása nekem akkoriban legalább akkora örömöt okozott, mint amit manapság mondjuk egy új Apple MacBook Pro kicsomagolása okoz. Sajnos az eredeti gép nincs már meg, legfőképp azért, mert időközben ZX Spectrum+-á alakult át egy Németországból hozott kit segítségével és így már csak ebben a formában maradhatott fenn.

<div class="rightbox" style="width:20%;"><a href="https://spectrumcomputing.co.uk/index.php?cat=96&id=5383"><img class="shadow" src="https://ia600604.us.archive.org/zipview.php?zip=/1/items/World_of_Spectrum_June_2017_Mirror/World%20of%20Spectrum%20June%202017%20Mirror.zip&file=World%20of%20Spectrum%20June%202017%20Mirror/sinclair/games-maps/t/Transversion.png" alt="Levels"></a></div>

Na, de nem is is erről a részről akartam most írni, hanem arról, hogy az egyik és máig kedvenc jákékom ZX Spectrum-on, az Ocean Software Ltd. cég által kiadott nagyon egyszerű [Transversion](https://spectrumcomputing.co.uk/index.php?cat=96&id=5383) nevű játéka volt. Maga a játék nincs nagyon túlbonyolítva és nincs is túl sok pálya benne, de mégis szórakoztató. 

Az azóta eltelt idők során időről időre keresgéltem az interneten újabb klónjait ennek a játéknak, és vannak / voltak is jó megoldások.

Végül álljon itt egy saját próbálkozásom, amit én most [PICO-8](https://www.lexaloffle.com/pico-8.php) platformon követtem el. Maga a [PICO-8](https://www.lexaloffle.com/pico-8.php) is megérne egy hosszabb bejegyzést, mert nagyon szórakoztató dolog egy modern számítógépen ilyen eszközzel dolgozni, de felfogni is csak nagyon nehezen tudom, hogy még egy ilyen egyszerű játékhoz is mennyi munka kellhetett anno, hogy Z80 assembly-ben, az akkori eszközökkel ilyen szépen meg tudják ezt csinálni.

<div class="shadow" style="width: 50%; margin-bottom: .5em; margin-right: .7em; float: left;">

<canvas class="emscripten" id="canvas" oncontextmenu="event.preventDefault()"></canvas>

<script type="text/javascript">
	var canvas = document.getElementById( "canvas" );
	canvas.width = window.innerWidth;
	canvas.height = window.innerHeight;

	// show Emscripten environment where the canvas is
	// arguments are passed to PICO-8
	
	var Module = {};
	Module.canvas = canvas;
	
	/*
		// When pico8_buttons is defined, PICO-8 takes each int to be a live bitfield
		// representing the state of each player's buttons
		
		var pico8_buttons = [0, 0, 0, 0, 0, 0, 0, 0]; // max 8 players
		pico8_buttons[0] = 2 | 16; // example: player 0, RIGHT and Z held down
		
		// when pico8_gpio is defined, reading and writing to gpio pins will
		// read and write to these values
		var pico8_gpio = new Array(128);
	*/

</script>

<script async type="text/javascript" src="js/transversion.js"></script>
  
<script>
	// key blocker. prevent cursor keys from scrolling page while playing cart.
	
	function onKeyDown_blocker(event) {
		event = event || window.event;
		var o = document.activeElement;
		if ( !o || o == document.body || o.tagName == "canvas" )
		{
			if ( [32, 37, 38, 39, 40].indexOf( event.keyCode ) > -1 )
			{
				if ( event.preventDefault ) event.preventDefault();
			}
		}
	}

	document.addEventListener( 'keydown', onKeyDown_blocker, false );

</script>

<br>

<center>

<div class="pico8_el" onclick="Module.pico8Reset();"><img style="width: 10px;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAAaklEQVR4Ae2dOwoAMQhE15A+rfc/3bZ7AlMnQfywCkKsfcgMM9ZP+QHtIn0vLeBAFduiFdQ/0DmvtR5LXJ6CPSXe2ZXcFNlTxFbemKrbZPs35XogeS9xeQr+anT6LzoOwEDwZJ7jwhXUnwkTTiDQ2Ja34AAAABB0RVh0TG9kZVBORwAyMDExMDIyMeNZtsEAAAAASUVORK5CYII=" alt="Reset" />
Reset</div>

<div class="pico8_el" onclick="Module.pico8TogglePaused();"><img style="width: 10px;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAAPUlEQVR4Ae3doQ0AIAxEUWABLPtPh2WCq26DwFSU/JPNT166QSu/Hg86W9dwLte+diP7AwAAAAAAgD+A+jM2ZAgo84I0PgAAABB0RVh0TG9kZVBORwAyMDExMDIyMeNZtsEAAAAASUVORK5CYII=" alt="Pause" />
Pause</div>

<div class="pico8_el" onclick="Module.requestFullScreen(true, false);"><img style="width: 10px;"  src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAAaklEQVR4Ae2dsQ1AIQhExfze1v2ns3UCrfgFhmgUUAoGgHscp21wX9BqaZoDojbB96OkDJKNcTN2BHTyYNYmoT2BlPL7BKgcPfHjAVXKKadkHOn9K1r16N0czN6a95N8mnA7Aq2fTZ3Af3UKmCSMazL8HwAAABB0RVh0TG9kZVBORwAyMDExMDIyMeNZtsEAAAAASUVORK5CYII=" alt="Fullscreen" />
Fullscreen</div>

<div class="pico8_el" onclick="Module.pico8ToggleSound();"><img style="width: 10px;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAAXklEQVR4Ae2doQ4AIQxD4YLH8v9fh+ULhjpxxSwLg2uyapr1JRu1iV5Z+1BGl4+xNpX38SYo2uRvYiT5LwEmt+ocgXVLrhPEgBiw8Q5w7/kueSkK+D2tJO4E/I3GrwkqQCBabEj/4QAAABB0RVh0TG9kZVBORwAyMDExMDIyMeNZtsEAAAAASUVORK5CYII=" alt="Toggle Sound" />
Sound</div>

<div class="pico8_el"><a target="_new" href="http://www.lexaloffle.com/bbs/?cat=7&sub=2"><img style="width: 10px;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAAlElEQVR4Ae2dMQ5FQBCGh6jcwAkkateg3DiAa+iQUGqVKi95FQfAJRQOoHeBUf8JyQqKjZ1uMzuz2e/LTE3KhyF7kSlgLOykas23f6D+A9Yp84aAOYU15pcJnfji0Il2ID8HzC4y38ZrnfIBGxeRoR3c3EWrACdsV5BOsx7OSRnrOXh4F5HzA6bevwUn8wlz7eCDsQM99B3ks0s/4QAAABB0RVh0TG9kZVBORwAyMDExMDIyMeNZtsEAAAAASUVORK5CYII=" alt="More Carts"/>
Carts</a></div>

</center>

</div>

asasalsk ask akls kalsla lslakslakls la s