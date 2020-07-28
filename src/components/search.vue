<template>
    <div>
        <div class="row justify-content-center form-inline ">
            <form class="form-inline">
                <div class="form-inline">
                    <div >
                        <input type="text"
                               class=" form-control" id="search"
                               placeholder="enter your song's name"
                               v-model.lazy="songName">
                    </div>
                </div>
            </form>
            <button class="btn btn-outline-light" @click="search">search</button>
        </div>
        <div style="height: 25px">
            <transition name="slide"  mode="out-in">
                <div class="warning justify-content-center text-danger" v-if="showWarning">
                    {{ warningText }}
                </div>
            </transition>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return{
                warningText: 'Please Enter a Song Name First',
                showWarning : false
            }
        },
        props:['songName'],
        methods: {
            search(){
                if(this.songName !== ''){
                    this.showWarning = false;
                    this.$emit('SearchButtonClicked', this.songName);
                }else {
                    this.showWarning = true;
                }
            }
        }
    }
</script>
<style>
    .warning {
        align-content: center;
        text-align: center;
    }
    .slide-enter{
        opacity: 0;

    }
    .slide-enter-active{
        animation: slide-in .4s ease-out forwards;
        transition: opacity .4s;
    }
    .slide-leave{

    }
    .slide-leave-active{
        animation: slide-out .4s ease-out forwards;
        transition: opacity .4s;
        opacity: 0;
    }

    @keyframes slide-in {
        from {
            transform: translateX(20px);
        }
        to {
            transform: translateX(0px);
        }
    }
    @keyframes slide-out {
        from {
            transform: translateX(0px);
        }
        to {
            transform: translateX(-20px);
        }
    }
</style>
