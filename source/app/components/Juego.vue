<template lang="pug">

#juego
	Tetronomo(:tetro="activo" v-if="activo.tetro")
	.tablero
		.filas(
			v-for="fila in tablero"
		)
			.columna(
				v-for="col in fila"
				:class="{fill : col == 1}"
			)


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
			tablero:[],
			activo:{
				posX: 0,
				posY: 0,
				rot: 0,
				tetro: null
			},
			estaticos:[

			],
			tetronomos:{
				j:{
					forma:[
						[[0,1,0],[0,1,0],[1,1,0]],
						[[0,0,0],[1,0,0],[1,1,1]],
						[[1,1,0],[1,0,0],[1,0,0]],
						[[1,1,1],[0,0,1],[0,0,0]],
					],
					color: "",
					img: ""
				}
			}
		}
	},
	mounted(){
		this.armarTablero()
		this.activo.tetro = this.tetronomos.j
	},
	methods:{
		armarTablero(){
			let columnas = 10
			let filas = 20
			for(let fila = 0; fila < filas; fila++){
				let filaP = []
				for(let col = 0; col < columnas; col++){
					filaP.push(0)
				}
				this.tablero.push(filaP)
			}
		}
	}
}
</script>

<style lang="sass">
.filas
	display: flex

.columna
	width: 50px
	height: 50px
	border: 1px solid black

</style>
