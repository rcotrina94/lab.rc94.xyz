---
---
<style>
	#main_content {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	column {
		display: flex;
		/* flex: 1 0; */
	}
</style>
<div class="column">
	{% for i in (1..25) %}
	```
	Spacer
	```
	{% endfor %}
</div>
<div class="column">
	<div class="cube">
		<div class="cube__face cube__face--front">front</div>
		<div class="cube__face cube__face--back">back</div>
		<div class="cube__face cube__face--right">right</div>
		<div class="cube__face cube__face--left">left</div>
		<div class="cube__face cube__face--top">top</div>
		<div class="cube__face cube__face--bottom">bottom</div>
	</div>
</div>

