<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8" />
<title>svg animation</title>
<style>
	html, body {
		width: 100%;
		height: 100%;
		padding: 0;
		margin: 0;
	}
	body {
		background-color: rgba(100,100,100,0.2);
		overflow: hidden;
	}

	#wrapper {
		width: 100%;
		min-height: 100%;
		margin: 0 auto;
		position: relative;
	}

	#pp {
		width: 100px;
		height: 100px;
		background-color: rgba(100,0,0,0.3);
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		margin: 0 auto;
	}

	svg {
		outline: 1px solid blue;
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		margin: 0 auto;
		width: 100%;
		height: 100%;
	}
</style>
</head>

<body>
	<div id="wrapper">
		<p id="status1"></p>
		<p id="status2"></p>
		<p id="pp_size"></p>
		<div id="pp"></div>
		<svg id="mysvg" width="300" height="300"></svg>
	</div><!--/#wrapper-->
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
	<script>
		$(document).ready(function(){
			var d = document;
			var mysvg = d.getElementById("mysvg");

			var mx,my,timer,random,mdpt,yini,input;

			setInterval(function() {
				//document size
				var svgw = $("svg").width();
				var svgh = $("svg").height();

				mdpt = svgw/2;
				yini = svgh-100;

				//random numbers
				random = {
					a: Math.floor(Math.random()*25),
					b: Math.floor(Math.random()*25),
					c: Math.floor(Math.random()*25),
					d: Math.floor(Math.random()*25),
					e: Math.floor(Math.random()*25)
				};

				mysvg.addEventListener("mousemove", function(e) {
					mx = e.clientX;
					my = e.clientY;

					mxabs = mx - mdpt;
					myabs = my - yini;

					mxabs_m = (mxabs/2);
					myabs_m = (myabs/2);

					input = '<path d="M ' + mdpt + ' ' + yini + 
						 ' l ' + 0 + ',' + 0 + ' ' +
						 		mxabs_m + ',' + (myabs_m*random.a) + ' ' +
						 		mxabs + ',' + myabs + ' ' +
						 '" stroke="red" stroke-width="7" stroke-linejoin="round" fill="none" />';
					$("#status2").html(random.a);
				});

				$("#status1").html("X coord: " + mx + "<br>Y coord: " + my + "<br><br>mid point: " + mdpt + "<br><br>width: " + svgw + "<br>height: " + svgh + "<br><br>random a: " + random.a + "<br>random b: " + random.b + "<br>random c: " + random.c);

				$("#mysvg").html(input);
			}, 10);
		});
	</script>
</body>
</html>
