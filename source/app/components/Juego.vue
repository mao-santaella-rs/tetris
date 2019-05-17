<template lang="pug">

#juego
	a(@click="mover") mover
	Tetronomo(:tetro="activo" v-if="activo.tetro")
	.tablero
		.filas(
			v-for="fila in tablero"
		)
			.columna(
				v-for="col in fila"
				:class="{fill : col.cuadro}"
			)
				span {{col.fila}}-{{col.col}}


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
			tabla:{
				columnas: 10,
				filas: 20
			},
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
	computed:{
		tablero(){
			let tablero = []
			for(let fila = 0; fila < this.tabla.filas; fila++){
				let filaP = []
				for(let col = 0; col < this.tabla.columnas; col++){
					filaP.push({
						fila: fila,
						col: col,
						cuadro: false
					})
				}
				tablero.push(filaP)
			}
			if(this.activo.tetro){
				let tetro = this.activo.tetro.forma[this.activo.rot]
				for(let fila = 0; fila < tetro.length; fila++){
					for(let col = 0; col < tetro[fila].length; col++){
						if(tetro[fila][col] === 1) {
							tablero[this.activo.posY + fila][this.activo.posX + col].cuadro = true
						}
					}
				}
			}
			return tablero
		}
	},
	mounted(){
		this.activo.tetro = this.tetronomos.j
	},
	methods:{
		mover(dir){
			this.activo.posY++
		},
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
