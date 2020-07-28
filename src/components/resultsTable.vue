<template>
    <div>
        <div>
            <hr class="bg-light">
            <p class="text-light display-4" style="text-shadow: 0 0 10px #000000; font-size: 30px">Results for <strong>{{ searchedSong }}</strong>:</p>
            <div  v-for="(result, index) in songItem" class="" >
                <div class="result-item row d-flex">
                    <div class="result-item_number display-4 ">
                        {{index+1}}
                    </div>
                    <div class="result-item-song-name display-4 flex-grow-1">
                        {{ result }}
                    </div>
                    <div>
                        <button @click="goToLyric" class="result-item-button btn btn-sm">show lyric</button>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
            }
        },
        props: ['searchedSong','songItem'],
        methods: {
            goToLyric() {
                this.$emit('goToLyric', 'lyricArea')
            }
        }
    }
</script>
<style>
    .result-item-song-name{
        font-size: 30px;
    }
    .result-item_number {
        font-size: 30px;
        padding-right: 15px;
        margin-right: 15px;
        border-right: solid gray 1px;
    }

    .result-item-button{
        height: 40px;
        border-radius: 20px;
        background-color: #00000055;
        border: white solid 1px;
        color: white;
        padding-left: 15px;
        padding-right: 15px;
    }
    .result-item-button:hover {
        background-color: #ffffffcc;
        color: black;
    }
    .result-item {
        margin: 10px 0 ;
        padding: 30px;
        height: 100px;
        background-color: #00000060;
        border-radius: 15px;
        color: white;
    }
    .result-item:hover {
        background-color: #00000066;

    }
</style>