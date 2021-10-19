---
---
<style>
	html, body {
		height: 100%;
	}
	#main_content {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	.scroll-area {
		min-height: 500vh;
		display: flex;
		width: 100%;
		flex-direction: column;
		align-items: center;
	}
	.scene {
		border: 4px dashed rgba(255, 255, 255, 0.25);
		position: sticky;
		top: 64px;
	}
	.cube {
		width: 200px;
		height: 200px;
		position: relative;
		transform-style: preserve-3d;
		/* transition: transform 0.1s; */
		transform-origin: center center;
	}
	.cube__face {
		position: absolute;
		width: 200px;
		height: 200px;
		border: 4px solid black;
		box-sizing: border-box;
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
<div class="scroll-area">
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

<script>
	document.body.addEventListener('touchmove', onScroll);
	window.addEventListener('scroll', onScroll);

	var cube = document.getElementById('cube');

	function getScrollPosition() { return window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop || 0; }
	var maxScroll = document.body.scrollHeight - window.innerHeight;

	function onScroll(){
		var ratio = getScrollPosition() / maxScroll;
		cube.style.transform = 'rotate3d(3,9,8,'+ Math.min(ratio * 360, 360) + 'deg)';
	}

	window.addEventListener('resize', function(){
		maxScroll = document.body.scrollHeight - window.innerHeight;
	});
</script>
