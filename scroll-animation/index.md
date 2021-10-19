---
---
<style>
	html, body {
		height: 100%
	}
	#main_content {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	.column {
		display: flex;
		flex-direction: column;
		/* flex: 1 0; */
	}
	.scene {
		position: sticky;
		top: 0px;
	}
	.cube {
		width: 200px;
		height: 200px;
		position: relative;
		transform-style: preserve-3d;
		transition: transform 1s;
		transform-origin: center center;
	}
	/*
	.cube.show-front  { transform: rotateY(   0deg); }
	.cube.show-right  { transform: rotateY( -90deg); }
	.cube.show-back   { transform: rotateY(-180deg); }
	.cube.show-left   { transform: rotateY(  90deg); }
	.cube.show-top    { transform: rotateX( -90deg); }
	.cube.show-bottom { transform: rotateX(  90deg); } */

	.cube__face {
		position: absolute;
		width: 200px;
		height: 200px;
		border: 2px solid black;
		line-height: 200px;
		font-size: 40px;
		font-weight: bold;
		color: white;
		text-align: center;
	}

	.cube__face--front  { background: hsla(  0, 100%, 50%, 0.7); }
	.cube__face--right  { background: hsla( 60, 100%, 50%, 0.7); }
	.cube__face--back   { background: hsla(120, 100%, 50%, 0.7); }
	.cube__face--left   { background: hsla(180, 100%, 50%, 0.7); }
	.cube__face--top    { background: hsla(240, 100%, 50%, 0.7); }
	.cube__face--bottom { background: hsla(300, 100%, 50%, 0.7); }

	.cube__face--front  { transform: rotateY(  0deg) translateZ(100px); }
	.cube__face--right  { transform: rotateY( 90deg) translateZ(100px); }
	.cube__face--back   { transform: rotateY(180deg) translateZ(100px); }
	.cube__face--left   { transform: rotateY(-90deg) translateZ(100px); }
	.cube__face--top    { transform: rotateX( 90deg) translateZ(100px); }
	.cube__face--bottom { transform: rotateX(-90deg) translateZ(100px); }
</style>
<div class="column">
	{% for i in (1..50) %}
		<blockquote>Spacer</blockquote>
	{% endfor %}
</div>
<div class="column">
	<div class="scene">
		<div id="cube" class="cube">
			<div class="cube__face cube__face--front">front</div>
			<div class="cube__face cube__face--back">back</div>
			<div class="cube__face cube__face--right">right</div>
			<div class="cube__face cube__face--left">left</div>
			<div class="cube__face cube__face--top">top</div>
			<div class="cube__face cube__face--bottom">bottom</div>
		</div>
	</div>
</div>

<script src="//cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.7/ScrollMagic.min.js"></script>
<script>
	document.body.addEventListener('touchmove', onScroll);
	window.addEventListener('scroll', onScroll);

	var cube = document.getElementById('cube');

	function getScrollPosition() { return window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop || 0; }
	var maxScroll = document.body.scrollHeight - window.innerHeight;

	function onScroll(){
		var ratio = getScrollPosition() / maxScroll;
		console.log(ratio);
		cube.style.transform = 'rotate3d(1,1,1,'+ Math.min(ratio * 360, 360) + 'deg) translateZ(100px)';
	}

</script>

