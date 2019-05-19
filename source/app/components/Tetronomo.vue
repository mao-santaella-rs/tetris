<template lang="pug">
.tetronomo
	.tet-fila(
		v-for="fila in tetro.tetro.forma[tetro.rot]"
	)
		.tet-block(
			v-for="block in fila"
			:class="{fill : block == 1}"
		)

</template>

<script>
export default {
	name: "Tetronomo",
	props:{
		tetro:{
			type: Object,
			default: () => ({})
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