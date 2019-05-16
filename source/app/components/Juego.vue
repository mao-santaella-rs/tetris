<template lang="pug">

#juego
	h1 Hola Mao
	Tetronomo

</template>

<script>
import Tetronomo from "./Tetronomo"
export default {
	name: "Juego",
	components:{
		Tetronomo
	},
	data(){
		return{
			tablero:[]
		}
	},
	mounted(){
		this.armarTablero()
	},
	methods:{
		armarTablero(){
			let columnas = 10
			let filas = 20
			for(let fila = 1; fila <= filas; fila++){
				let filaP = []
				for(let col = 1; col <= columnas; col++){
					filaP.push(0)
				}
				this.tablero.push(filaP)
			}
		}
	}
}
</script>

<style lang="sass">

</style>
