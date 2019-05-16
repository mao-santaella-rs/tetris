<template lang="pug">
.tetronomo
	.tet-fila(
		v-for="fila in j.forma"
	)
		.tet-block(
			v-for="block in fila"
			:class="{fill : block == 1}"
		)

</template>

<script>
export default {
	name: "Tetronomo",
	data(){
		return{
			j:{
				forma: [
					[0,0,1,0],
					[0,0,1,0],
					[0,1,1,0],
					[0,0,0,0]
				],
				color: "rojo"
			}
		}
	}
}
</script>

<style lang="sass">
.tet-fila
	display: flex
.tet-block
	height: 20px
	width: 20px

.fill
	background-color: red

</style>