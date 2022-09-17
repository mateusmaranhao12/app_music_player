<template>
    <div v-if="!PlayerVisivel">
        <div class="text-green-400 font-bold text-center text-3xl mb-7 mt-3">
            App Music Player 
        </div>
        <div 
            v-for = "(som, somIndex) in lista_de_sons" :key="som.id"
            class="flex flex-row justify-between mb-4 cursor-pointer"
            @click="play(somIndex)"
        >
            <div>
                <span class="text-green-200">{{som.nome}}</span>
                <br />
                <span class="text-emerald-400 text-xs">
                    {{som.artista}} -
                    <span class="text-green-500">
                        {{som.ano}}
                    </span>
                </span>
            </div>
            <div>
                <img 
                    class="max-h-12 rounded"
                    :src="som.imagem"
                >
            </div>
        </div>
    </div>
    <div v-if="PlayerVisivel">
        <player 
            :som="lista_de_sons[somAtual]"
            @voltar="PlayerVisivel = !PlayerVisivel"
            @proxima="proximaMusica"
            @anterior="musicaAnterior"
        />
    </div>
</template>

<script>

    import Player from './Player.vue';

    export default {

        name: 'ListaDeSons',

        components: {
            Player
        },

        data () {
            return {

                PlayerVisivel: false,
                somAtual: 0,
                
                lista_de_sons: [
                    {
                        id: 1,
                        nome: 'Dia Azul',
                        artista: 'Teto',
                        ano: 2021,
                        imagem: require ('../assets/m1.jpg'),
                        som: require('../assets/m1.mp3')
                    },
                    {
                        id: 2,
                        nome: 'Counting Stars',
                        artista: 'One Republic',
                        ano: 2013,
                        imagem: require ('../assets/m2.jpg'),
                        som: require('../assets/m2.mp3')
                    },
                    {
                        id: 3,
                        nome: 'Symbolism',
                        artista: 'Electro',
                        ano: 2015,
                        imagem: require ('../assets/m3.jpg'),
                        som: require('../assets/m3.mp3')
                    }
                ]

            }
        },

        methods: {

            play(index) {
                this.somAtual = index
                this.PlayerVisivel = true
            },

            proximaMusica() {
                if (this.somAtual < this.lista_de_sons.length - 1) {
                    this.somAtual += 1
                } else {
                    this.somAtual = 0
                }
            },

            musicaAnterior() {
                if (this.somAtual != 0) {
                    this.somAtual -= 1
                } else {
                    this.somAtual = this.lista_de_sons.length - 1
                }
            },

        }
    }

</script>