<script>
	import { defineComponent } from 'vue';
	import SelectDeselectTwoLists from '@/selectDeselectTwoLists.vue';

	export default defineComponent({
		name: 'ServeDev',
		components: {
			SelectDeselectTwoLists,
		},
	});
</script>

<template>
	<section id="app" class="container">
		<form>
			<div class="row">
				<div class="column column-20"></div>
				<div class="column column-60">
					<SelectDeselectTwoLists/>
				</div>
				<div class="column column-20"></div>
			</div>
		</form>
	</section>
</template>

<style>
	@import '//fonts.googleapis.com/css?family=Roboto:300,300italic,700,700italic';
	@import '//cdnjs.cloudflare.com/ajax/libs/normalize/5.0.0/normalize.css';
	@import 'https://cdnjs.cloudflare.com/ajax/libs/milligram/1.4.1/milligram.min.css';
	#app {
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>
