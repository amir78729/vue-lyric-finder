<template>
    <div>

        <div class="container-fluid text-light lyric-border" style="margin-top: 30px">
            <div class="row d-flex">
                <div class="flex-grow-1">
                    <h1 style="font-size: 40px" class="display-1">{{ lyricSongName }}</h1>
                    <h2 style="font-size: 20px"  class="display-3">Artist Name</h2>
                </div>
                <div>
                    <button class="btn btn-sm result-item-button"
                            @click="goBack"
                            style="margin-top: 0px">Go Back</button>
                </div>
            </div>
            <!--        <hr class="bg-light">-->
            <div class="lyric">
                Blank face in the windowpane
                Made clear in seconds of light
                Disappears and returns again
                Counting hours, searching the night
                Might be waiting for someone
                Might be there for us to see
                Might be in need of talking
                Might be staring directly at me
                Inside plays a lullaby
                Slurred voice over children cries
                On the inside
                Haunting loneliness in the eye
                Skin covering a secret scar
                His hand is waving a goodbye
                There's no response or action returned
                There is deep prejudice in me
                Outshines all reason inside
                Given dreams all ridden with pain
                And projected unto the last
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        props: ['lyricSongName']
        ,
        data() {
            return {
                lyric: ''
            }
        },methods: {
            goBack() {
                this.$emit('goBack', 'resultsTableArea')
            }
        }
    }
</script>
<style>
    .lyric {
        white-space: pre-line;
    }

    .lyric-border{
        background-color: #00000055;
        padding: 50px;
        border-radius: 20px
    }
    .lyric-border:hover{
        background-color: #00000066;
    }
    .result-item-button{
        height: 40px;
        border-radius: 20px;
        background-color: #00000060;
        border: white solid 1px;
        color: white;
        padding-left: 15px;
        padding-right: 15px;
    }
    .result-item-button:hover {
        background-color: #ffffffcc;
        color: black;
    }
</style>

