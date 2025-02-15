# Jadwal Shalat
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Prayer Time</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
 <link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css"> 
  
  <script src="css/jquery.min.js"></script>
  <script src="css/bootstrap.min.js"></script>
  
  <!-- Template Main CSS File -->
  <link href="css/style.css" rel="stylesheet">
  
  <!-- PRAYER TIME -->

	
  <script type="text/javascript">
		
		function waktuSholat() {
  			var today = new Date();
  			var h = today.getHours();
  			var m = today.getMinutes();
  			var s = today.getSeconds();
  			h = checkTime(h);
  			m = checkTime(m);
  			s = checkTime(s);
  			
  			var date = today.getDate();
  			var month = today.getMonth();
  			var montharr =["Januari","Februari","Maret","April","Mei","Juni","Juli","Agustus","September","Oktober","November","Desember"];
  			month=montharr[month];
  			var year = today.getFullYear();
	  
	  		var day = today.getDay();
	  		var dayarr =["Minggu","Senin","Selasa","Rabu","Kamis","Jumat","Sabtu"];
	  		day=dayarr[day];
  			
  			document.getElementById('jam').innerHTML = h + ":" + m + ":" + s;
  			document.getElementById('hari').innerHTML = day+",";
  			document.getElementById('tgl').innerHTML = date+" "+month+" "+year;
  			
  			
  			// MANUAL SETTINGS --------------------------------------------------------
  			prayTimes.setMethod('MWL'); // perhitungan
  			var Ptimes = prayTimes.getTimes(today, [-6.2, 106.8], 7); // jakarta (longitude, Latitude, Time Zone)
  			// ------------------------------------------------------------------------
  			
  			document.getElementById('subuh').innerHTML =   Ptimes.fajr;
  			document.getElementById('terbit').innerHTML =  Ptimes.sunrise;
  			document.getElementById('zuhur').innerHTML =   Ptimes.dhuhr;
  			document.getElementById('ashar').innerHTML =   Ptimes.asr;
  			document.getElementById('maghrib').innerHTML = Ptimes.maghrib;
  			document.getElementById('isya').innerHTML =    Ptimes.isha;
  			
			// Azan
  			
  			var waktu = h + ":" + m;

  			if (waktu == Ptimes.fajr) {
  				$('#ModalAzan').modal('show');

				setTimeout(function() {
    				$('#ModalAzan').modal('hide');
				}, 60000);
			}
  			
  			if (waktu == Ptimes.dhuhr) {
  				$('#ModalAzan').modal('show');

				setTimeout(function() {
    				$('#ModalAzan').modal('hide');
				}, 60000);
			}
  			
			if (waktu == Ptimes.asr) {
  				$('#ModalAzan').modal('show');

				setTimeout(function() {
    				$('#ModalAzan').modal('hide');
				}, 60000);
			}
			
			if (waktu == Ptimes.maghrib) {
  				$('#ModalAzan').modal('show');

				setTimeout(function() {
    				$('#ModalAzan').modal('hide');
				}, 60000);
			}
			
			if (waktu == Ptimes.isha) {
  				$('#ModalAzan').modal('show');

				setTimeout(function() {
    				$('#ModalAzan').modal('hide');
				}, 60000);
			}
			
			// colors
			
			var akhirwaktu = "23:59";
			
			if (waktu  >= Ptimes.fajr && waktu < Ptimes.sunrise) {
  				document.getElementById('csubuh').style.backgroundColor = "red";
			} else {
  				document.getElementById('csubuh').style.backgroundColor = "white";
			}
			
			if (waktu  >= Ptimes.sunrise && waktu < Ptimes.dhuhr) {
  				document.getElementById('cterbit').style.backgroundColor = "red";
			} else {
  				document.getElementById('cterbit').style.backgroundColor = "white";
			}
			
			if (waktu  >= Ptimes.dhuhr && waktu < Ptimes.asr) {
  				document.getElementById('czuhur').style.backgroundColor = "red";
			} else {
  				document.getElementById('czuhur').style.backgroundColor = "white";
			}
			
			if (waktu  >= Ptimes.asr && waktu < Ptimes.maghrib) {
  				document.getElementById('cashar').style.backgroundColor = "red";
			} else {
  				document.getElementById('cashar').style.backgroundColor = "white";
			}
			
			if (waktu  >= Ptimes.maghrib && waktu < Ptimes.isha) {
  				document.getElementById('cmaghrib').style.backgroundColor = "red";
			} else {
  				document.getElementById('cmaghrib').style.backgroundColor = "white";
			}
			if (waktu  >= Ptimes.isha && waktu < akhirwaktu) {
  				document.getElementById('cisya').style.backgroundColor = "red";
			} else {
  				document.getElementById('cisya').style.backgroundColor = "white";
			}
  			
  			var t = setTimeout(waktuSholat, 1000);
		}
		function checkTime(i) {
  			if (i < 10) {i = "0" + i};  // add zero in front of numbers < 10
  			return i;
		}
		
   </script>
	
</head>

<body onload="waktuSholat()">
<div class="w3-container">
<header class="w3-container w3-teal">
  <h1>Jadwal Shalat</h1>
</header>
  		<div class="w3-container w3-green">
			<span id="hari"></span>
			<span id="tgl"></span>
			<span id="jam"></span>
		</div>
  	


	
	<!-- Modal Azan-->
  	<div class="w3-panel w3-blue w3-modal" id="ModalAzan">
    	<div class="modal-dialog modal-dialog-centered modal-lg">
      		<div class="modal-content">
        		<div class="modal-header" style="padding:30px 90px;">
          			<h1>Memasuki Waktu Azan</h1>
        		</div>
        		<div class="modal-body">
          			<img src="img/azan.jpg" > 
        		</div>
      		</div>
    	</div> 
    </div>
    

   

     
    <div id="csubuh" class="w3-panel w3-green w3-round-large"> 
    	
      	<h1>SUBUH</h1>
      	<h1><div class="w3-display-container" id="subuh"></div></h1>
    </div>
    <div id="cterbit" class="w3-panel w3-green w3-round-large"> 
    	
      	<h1>TERBIT</h1>
      	<h1><div class="w3-display-container" id="terbit"></div></h1>
    </div>
    <div id="czuhur" class="w3-panel w3-green w3-round-large"> 
    	
      	<h1>ZUHUR</h1>        
      	<h1><div class="w3-display-container" id="zuhur"></div></h1>
    </div>
    <div id="cashar" class="w3-panel w3-lime w3-round-xlarge"> 
    	
      	<h1>ASHAR</h1>
      	<h1><div id="ashar"></div></h1>
    </div>
    <div id="cmaghrib" class="w3-panel w3-lime w3-round-xlarge"> 
    	 
      	<h1>MAGHRIB</h1>
      	<h1><div id="maghrib"></div></h1>
    </div>
    <div id="cisya" class="w3-panel w3-lime w3-round-xlarge"> 
    		<h1>ISYA</h1>        
      	<h1><div id="isya"></div></h1>
    </div>
  </div>
</div>
</div>

</body>
</html>

 <script type="text/javascript">
//--------------------- Copyright Block ----------------------
/* 

PrayTimes.js: Prayer Times Calculator (ver 2.3)
Copyright (C) 2007-2011 PrayTimes.org

Developer: Hamid Zarrabi-Zadeh
License: GNU LGPL v3.0

TERMS OF USE:
	Permission is granted to use this code, with or 
	without modification, in any website or application 
	provided that credit is given to the original work 
	with a link back to PrayTimes.org.

This program is distributed in the hope that it will 
be useful, but WITHOUT ANY WARRANTY. 

PLEASE DO NOT REMOVE THIS COPYRIGHT BLOCK.
 
*/ 


//--------------------- Help and Manual ----------------------
/*

User's Manual: 
http://praytimes.org/manual

Calculation Formulas: 
http://praytimes.org/calculation



//------------------------ User Interface -------------------------


	getTimes (date, coordinates [, timeZone [, dst [, timeFormat]]]) 
	
	setMethod (method)       // set calculation method 
	adjust (parameters)      // adjust calculation parameters	
	tune (offsets)           // tune times by given offsets 

	getMethod ()             // get calculation method 
	getSetting ()            // get current calculation parameters
	getOffsets ()            // get current time offsets


//------------------------- Sample Usage --------------------------


	var PT = new PrayTimes('ISNA');
	var times = PT.getTimes(new Date(), [43, -80], -5);
	document.write('Sunrise = '+ times.sunrise)


*/
	

//----------------------- PrayTimes Class ------------------------


function PrayTimes(method) {


	//------------------------ Constants --------------------------
	var
	
	// Time Names
	timeNames = {
		imsak    : 'Imsak',
		fajr     : 'Fajr',
		sunrise  : 'Sunrise',
		dhuhr    : 'Dhuhr',
		asr      : 'Asr',
		sunset   : 'Sunset',
		maghrib  : 'Maghrib',
		isha     : 'Isha',
		midnight : 'Midnight'
	},


	// Calculation Methods
	methods = {
		MWL: {
			name: 'Muslim World League',
			params: { fajr: 18, isha: 17 } },
		ISNA: {
			name: 'Islamic Society of North America (ISNA)',
			params: { fajr: 15, isha: 15 } },
		Egypt: {
			name: 'Egyptian General Authority of Survey',
			params: { fajr: 19.5, isha: 17.5 } },
		Makkah: {
			name: 'Umm Al-Qura University, Makkah',
			params: { fajr: 18.5, isha: '90 min' } },  // fajr was 19 degrees before 1430 hijri
		Karachi: {
			name: 'University of Islamic Sciences, Karachi',
			params: { fajr: 18, isha: 18 } },
		Tehran: {
			name: 'Institute of Geophysics, University of Tehran',
			params: { fajr: 17.7, isha: 14, maghrib: 4.5, midnight: 'Jafari' } },  // isha is not explicitly specified in this method
		Jafari: {
			name: 'Shia Ithna-Ashari, Leva Institute, Qum',
			params: { fajr: 16, isha: 14, maghrib: 4, midnight: 'Jafari' } }
	},


	// Default Parameters in Calculation Methods
	defaultParams = {
		maghrib: '0 min', midnight: 'Standard'

	},
 
 
	//----------------------- Parameter Values ----------------------
	/*
	
	// Asr Juristic Methods
	asrJuristics = [ 
		'Standard',    // Shafi`i, Maliki, Ja`fari, Hanbali
		'Hanafi'       // Hanafi
	],


	// Midnight Mode
	midnightMethods = [ 
		'Standard',    // Mid Sunset to Sunrise
		'Jafari'       // Mid Sunset to Fajr
	],


	// Adjust Methods for Higher Latitudes
	highLatMethods = [
		'NightMiddle', // middle of night
		'AngleBased',  // angle/60th of night
		'OneSeventh',  // 1/7th of night
		'None'         // No adjustment
	],


	// Time Formats
	timeFormats = [
		'24h',         // 24-hour format
		'12h',         // 12-hour format
		'12hNS',       // 12-hour format with no suffix
		'Float'        // floating point number 
	],
	*/	


	//---------------------- Default Settings --------------------
	
	calcMethod = 'MWL',

	// do not change anything here; use adjust method instead
	setting = {  
		imsak    : '10 min',
		dhuhr    : '0 min',  
		asr      : 'Standard',
		highLats : 'NightMiddle'
	},

	timeFormat = '24h',
	timeSuffixes = ['am', 'pm'],
	invalidTime =  '-----',

	numIterations = 1,
	offset = {},


	//----------------------- Local Variables ---------------------

	lat, lng, elv,       // coordinates
	timeZone, jDate;     // time variables
	

	//---------------------- Initialization -----------------------
	
	
	// set methods defaults
	var defParams = defaultParams;
	for (var i in methods) {
		var params = methods[i].params;
		for (var j in defParams)
			if ((typeof(params[j]) == 'undefined'))
				params[j] = defParams[j];
	};

	// initialize settings
	calcMethod = methods[method] ? method : calcMethod;
	var params = methods[calcMethod].params;
	for (var id in params)
		setting[id] = params[id];

	// init time offsets
	for (var i in timeNames)
		offset[i] = 0;

		
	
	//----------------------- Public Functions ------------------------
	return {

	
	// set calculation method 
	setMethod: function(method) {
		if (methods[method]) {
			this.adjust(methods[method].params);
			calcMethod = method;
		}
	},


	// set calculating parameters
	adjust: function(params) {
		for (var id in params)
			setting[id] = params[id];
	},


	// set time offsets
	tune: function(timeOffsets) {
		for (var i in timeOffsets)
			offset[i] = timeOffsets[i];
	},


	// get current calculation method
	getMethod: function() { return calcMethod; },

	// get current setting
	getSetting: function() { return setting; },

	// get current time offsets
	getOffsets: function() { return offset; },

	// get default calc parametrs
	getDefaults: function() { return methods; },


	// return prayer times for a given date
	getTimes: function(date, coords, timezone, dst, format) {
		lat = 1* coords[0];
		lng = 1* coords[1]; 
		elv = coords[2] ? 1* coords[2] : 0;
		timeFormat = format || timeFormat;
		if (date.constructor === Date)
			date = [date.getFullYear(), date.getMonth()+ 1, date.getDate()];
		if (typeof(timezone) == 'undefined' || timezone == 'auto')
			timezone = this.getTimeZone(date);
		if (typeof(dst) == 'undefined' || dst == 'auto') 
			dst = this.getDst(date);
		timeZone = 1* timezone+ (1* dst ? 1 : 0);
		jDate = this.julian(date[0], date[1], date[2])- lng/ (15* 24);
		
		return this.computeTimes();
	},


	// convert float time to the given format (see timeFormats)
	getFormattedTime: function(time, format, suffixes) {
		if (isNaN(time))
			return invalidTime;
		if (format == 'Float') return time;
		suffixes = suffixes || timeSuffixes;

		time = DMath.fixHour(time+ 0.5/ 60);  // add 0.5 minutes to round
		var hours = Math.floor(time); 
		var minutes = Math.floor((time- hours)* 60);
		var suffix = (format == '12h') ? suffixes[hours < 12 ? 0 : 1] : '';
		var hour = (format == '24h') ? this.twoDigitsFormat(hours) : ((hours+ 12 -1)% 12+ 1);
		return hour+ ':'+ this.twoDigitsFormat(minutes)+ (suffix ? ' '+ suffix : '');
	},


	//---------------------- Calculation Functions -----------------------


	// compute mid-day time
	midDay: function(time) {
		var eqt = this.sunPosition(jDate+ time).equation;
		var noon = DMath.fixHour(12- eqt);
		return noon;
	},


	// compute the time at which sun reaches a specific angle below horizon
	sunAngleTime: function(angle, time, direction) {
		var decl = this.sunPosition(jDate+ time).declination;
		var noon = this.midDay(time);
		var t = 1/15* DMath.arccos((-DMath.sin(angle)- DMath.sin(decl)* DMath.sin(lat))/ 
				(DMath.cos(decl)* DMath.cos(lat)));
		return noon+ (direction == 'ccw' ? -t : t);
	},


	// compute asr time 
	asrTime: function(factor, time) { 
		var decl = this.sunPosition(jDate+ time).declination;
		var angle = -DMath.arccot(factor+ DMath.tan(Math.abs(lat- decl)));
		return this.sunAngleTime(angle, time);
	},


	// compute declination angle of sun and equation of time
	// Ref: http://aa.usno.navy.mil/faq/docs/SunApprox.php
	sunPosition: function(jd) {
		var D = jd - 2451545.0;
		var g = DMath.fixAngle(357.529 + 0.98560028* D);
		var q = DMath.fixAngle(280.459 + 0.98564736* D);
		var L = DMath.fixAngle(q + 1.915* DMath.sin(g) + 0.020* DMath.sin(2*g));

		var R = 1.00014 - 0.01671* DMath.cos(g) - 0.00014* DMath.cos(2*g);
		var e = 23.439 - 0.00000036* D;

		var RA = DMath.arctan2(DMath.cos(e)* DMath.sin(L), DMath.cos(L))/ 15;
		var eqt = q/15 - DMath.fixHour(RA);
		var decl = DMath.arcsin(DMath.sin(e)* DMath.sin(L));

		return {declination: decl, equation: eqt};
	},


	// convert Gregorian date to Julian day
	// Ref: Astronomical Algorithms by Jean Meeus
	julian: function(year, month, day) {
		if (month <= 2) {
			year -= 1;
			month += 12;
		};
		var A = Math.floor(year/ 100);
		var B = 2- A+ Math.floor(A/ 4);

		var JD = Math.floor(365.25* (year+ 4716))+ Math.floor(30.6001* (month+ 1))+ day+ B- 1524.5;
		return JD;
	},

	
	//---------------------- Compute Prayer Times -----------------------


	// compute prayer times at given julian date
	computePrayerTimes: function(times) {
		times = this.dayPortion(times);
		var params  = setting;
		
		var imsak   = this.sunAngleTime(this.eval(params.imsak), times.imsak, 'ccw');
		var fajr    = this.sunAngleTime(this.eval(params.fajr), times.fajr, 'ccw');
		var sunrise = this.sunAngleTime(this.riseSetAngle(), times.sunrise, 'ccw');  
		var dhuhr   = this.midDay(times.dhuhr);
		var asr     = this.asrTime(this.asrFactor(params.asr), times.asr);
		var sunset  = this.sunAngleTime(this.riseSetAngle(), times.sunset);;
		var maghrib = this.sunAngleTime(this.eval(params.maghrib), times.maghrib);
		var isha    = this.sunAngleTime(this.eval(params.isha), times.isha);

		return {
			imsak: imsak, fajr: fajr, sunrise: sunrise, dhuhr: dhuhr, 
			asr: asr, sunset: sunset, maghrib: maghrib, isha: isha
		};
	},


	// compute prayer times 
	computeTimes: function() {
		// default times
		var times = { 
			imsak: 5, fajr: 5, sunrise: 6, dhuhr: 12, 
			asr: 13, sunset: 18, maghrib: 18, isha: 18
		};

		// main iterations
		for (var i=1 ; i<=numIterations ; i++) 
			times = this.computePrayerTimes(times);

		times = this.adjustTimes(times);
		
		// add midnight time
		times.midnight = (setting.midnight == 'Jafari') ? 
				times.sunset+ this.timeDiff(times.sunset, times.fajr)/ 2 :
				times.sunset+ this.timeDiff(times.sunset, times.sunrise)/ 2;

		times = this.tuneTimes(times);
		return this.modifyFormats(times);
	},


	// adjust times 
	adjustTimes: function(times) {
		var params = setting;
		for (var i in times)
			times[i] += timeZone- lng/ 15;
			
		if (params.highLats != 'None')
			times = this.adjustHighLats(times);
			
		if (this.isMin(params.imsak))
			times.imsak = times.fajr- this.eval(params.imsak)/ 60;
		if (this.isMin(params.maghrib))
			times.maghrib = times.sunset+ this.eval(params.maghrib)/ 60;
		if (this.isMin(params.isha))
			times.isha = times.maghrib+ this.eval(params.isha)/ 60;
		times.dhuhr += this.eval(params.dhuhr)/ 60; 

		return times;
	},


	// get asr shadow factor
	asrFactor: function(asrParam) {
		var factor = {Standard: 1, Hanafi: 2}[asrParam];
		return factor || this.eval(asrParam);
	},


	// return sun angle for sunset/sunrise
	riseSetAngle: function() {
		//var earthRad = 6371009; // in meters
		//var angle = DMath.arccos(earthRad/(earthRad+ elv));
		var angle = 0.0347* Math.sqrt(elv); // an approximation
		return 0.833+ angle;
	},


	// apply offsets to the times
	tuneTimes: function(times) {
		for (var i in times)
			times[i] += offset[i]/ 60; 
		return times;
	},


	// convert times to given time format
	modifyFormats: function(times) {
		for (var i in times)
			times[i] = this.getFormattedTime(times[i], timeFormat); 
		return times;
	},


	// adjust times for locations in higher latitudes
	adjustHighLats: function(times) {
		var params = setting;
		var nightTime = this.timeDiff(times.sunset, times.sunrise); 

		times.imsak = this.adjustHLTime(times.imsak, times.sunrise, this.eval(params.imsak), nightTime, 'ccw');
		times.fajr  = this.adjustHLTime(times.fajr, times.sunrise, this.eval(params.fajr), nightTime, 'ccw');
		times.isha  = this.adjustHLTime(times.isha, times.sunset, this.eval(params.isha), nightTime);
		times.maghrib = this.adjustHLTime(times.maghrib, times.sunset, this.eval(params.maghrib), nightTime);
		
		return times;
	},

	
	// adjust a time for higher latitudes
	adjustHLTime: function(time, base, angle, night, direction) {
		var portion = this.nightPortion(angle, night);
		var timeDiff = (direction == 'ccw') ? 
			this.timeDiff(time, base):
			this.timeDiff(base, time);
		if (isNaN(time) || timeDiff > portion) 
			time = base+ (direction == 'ccw' ? -portion : portion);
		return time;
	},

	
	// the night portion used for adjusting times in higher latitudes
	nightPortion: function(angle, night) {
		var method = setting.highLats;
		var portion = 1/2 // MidNight
		if (method == 'AngleBased')
			portion = 1/60* angle;
		if (method == 'OneSeventh')
			portion = 1/7;
		return portion* night;
	},


	// convert hours to day portions 
	dayPortion: function(times) {
		for (var i in times)
			times[i] /= 24;
		return times;
	},


	//---------------------- Time Zone Functions -----------------------


	// get local time zone
	getTimeZone: function(date) {
		var year = date[0];
		var t1 = this.gmtOffset([year, 0, 1]);
		var t2 = this.gmtOffset([year, 6, 1]);
		return Math.min(t1, t2);
	},

	
	// get daylight saving for a given date
	getDst: function(date) {
		return 1* (this.gmtOffset(date) != this.getTimeZone(date));
	},


	// GMT offset for a given date
	gmtOffset: function(date) {
		var localDate = new Date(date[0], date[1]- 1, date[2], 12, 0, 0, 0);
		var GMTString = localDate.toGMTString();
		var GMTDate = new Date(GMTString.substring(0, GMTString.lastIndexOf(' ')- 1));
		var hoursDiff = (localDate- GMTDate) / (1000* 60* 60);
		return hoursDiff;
	},

	
	//---------------------- Misc Functions -----------------------

	// convert given string into a number
	eval: function(str) {
		return 1* (str+ '').split(/[^0-9.+-]/)[0];
	},


	// detect if input contains 'min'
	isMin: function(arg) {
		return (arg+ '').indexOf('min') != -1;
	},


	// compute the difference between two times 
	timeDiff: function(time1, time2) {
		return DMath.fixHour(time2- time1);
	},


	// add a leading 0 if necessary
	twoDigitsFormat: function(num) {
		return (num <10) ? '0'+ num : num;
	}
	
}}



//---------------------- Degree-Based Math Class -----------------------


var DMath = {

	dtr: function(d) { return (d * Math.PI) / 180.0; },
	rtd: function(r) { return (r * 180.0) / Math.PI; },

	sin: function(d) { return Math.sin(this.dtr(d)); },
	cos: function(d) { return Math.cos(this.dtr(d)); },
	tan: function(d) { return Math.tan(this.dtr(d)); },

	arcsin: function(d) { return this.rtd(Math.asin(d)); },
	arccos: function(d) { return this.rtd(Math.acos(d)); },
	arctan: function(d) { return this.rtd(Math.atan(d)); },

	arccot: function(x) { return this.rtd(Math.atan(1/x)); },
	arctan2: function(y, x) { return this.rtd(Math.atan2(y, x)); },

	fixAngle: function(a) { return this.fix(a, 360); },
	fixHour:  function(a) { return this.fix(a, 24 ); },

	fix: function(a, b) { 
		a = a- b* (Math.floor(a/ b));
		return (a < 0) ? a+ b : a;
	}
}


//---------------------- Init Object -----------------------


var prayTimes = new PrayTimes();

</script>
