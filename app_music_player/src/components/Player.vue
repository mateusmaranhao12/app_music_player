<template>
    <audio :src="som.som" preload="auto" autoplay ref="audioPlayer"></audio>
    <div class="text-white">
        <div class="flex flex-row justify-between">
            <button @click="voltar"><i class="fa-solid fa-arrow-left"></i></button>
            <div class="text-green-400 font-bold text-center text-1xl">
                App Music Player
            </div>
        </div>

        <div>
            <img class="rounded mt-8 mb-4" :src="som.imagem">
            <div class="text-center">
                <p class="text-green-300 font-bold">{{som.nome}}</p>
                <p class="text-emerald-400">{{som.artista}} - {{som.ano}}</p>
            </div>
        </div>

        <div class="grid grid-cols-3 mt-10">
            <div class="flex items-center justify-center">
                <button @click="anterior"><i class="fa-solid fa-backward"></i></button>
            </div>
            <div  class="flex items-center justify-center">
                <button @click="tocarMusica" class="rounded-full bg-green-500 h-24 w-24 text-black font-bold">
                    <i :class="icone"></i>
                </button>
            </div>
            <div  class="flex items-center justify-center">
                <button @click="proxima"><i class="fa-solid fa-forward"></i></button>
            </div>
        </div>
    </div>
</template>

<script>


    export default {
        data () {
            return {
                tocando: true
            }
        },
        name: 'Player',
        props: {
            som: {
                id: Number,
                nome: String,
                artista: String,
                ano: Number,
                imagem: String,
                som: String
            }
        },

        emits: ['voltar', 'proxima', 'anterior'],

        methods: {

            voltar() {
                this.$emit('voltar')
            },

            tocarMusica() {
                if (this.tocando) {
                    this.$refs.audioPlayer.pause()
                } else {
                    this.$refs.audioPlayer.play()
                }

                this.tocando = !this.tocando
            },

            proxima() {
                this.$emit('proxima')
            },

            anterior() {
                this.$emit('anterior')
            },

        },

        computed: {

            icone() {
                if (this.tocando) {
                    return 'fa-solid fa-pause'
                } else {
                    return 'fa-solid fa-play'
                }
            }
            
        }
    }

</script>