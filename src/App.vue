<template>
    <div class="container-fluid">
        <nav  class="navbar justify-content-center  my-nav fixed-top">
            <h3 class="display-5 text-light">Lyric Finder</h3>
        </nav>
        <section>
            <transition name="fade" appear>
                <search-area
                    style="margin-top: 100px"
                    @SearchButtonClicked="loadResults($event)"
                    :song-name="songTitle"></search-area>
            </transition>
            <transition name="fade">
                <div class=" container col-md-8 col-sm-9 col-lg-7" v-if="searchButtonWasClicked">
                    <transition name="slide"  mode="out-in">
                        <component :is="selectedComponent"
                           :searchedSong="songTitle"
                           :songItem="results"
                           :lyricSongName="songTitle"
                           @goBack="selectedComponent = $event"
                           @goToLyric="selectedComponent = $event"></component>
                    </transition>
                </div>
            </transition>
            <div class="row justify-content-center max-vw">
                <table id="back-button-container" class="table table-hover table-striped results"></table>
            </div>
            <div class="row justify-content-center max-vw">
                <table id="results" class="table table-hover table-striped results">
                </table>
            </div>
        </section>
    </div>
</template>

<script>
    import search from "./components/search.vue"
    import resultsTable from "./components/resultsTable.vue"
    import lyric from "./components/lyric.vue"

    export default {
        data() {
            return {
                results: ['opeth','gojira','opeth','gojira','opeth','gojira','chartar'],
                songTitle: '',
                searchButtonWasClicked: false,
                selectedComponent: 'search'
            }
        },
        components: {
            searchArea: search,
            resultsTableArea: resultsTable,
            lyricArea: lyric
        },
        methods: {
            loadResults(event){
                console.log('search button clicked')
                this.songTitle = event;
                this.selectedComponent = 'resultsTableArea';
                this.searchButtonWasClicked = true;
            }
        }
    }
</script>

<style>
    .my-nav {
        background-color: #111111;
        opacity: 0.9;
    }
    .my-nav:hover {
        opacity: 0.95;
    }
    .search-box {
        padding: 20px;
        text-align: center;
        color: #D8D8F6;
        border-bottom: solid 1px #D8D8F6;
        max-width: 80vw;

    }

    .musixmatch-logo {
        text-align: center;

    }

    .musixmatch-logo a {
        color: inherit;
        text-decoration: none;
    }

    #search {
        border-radius: 10px;
    }

    #search:focus {
        outline: none;
        /*needed to be removed as the outline had square corners which interferes with border radius*/
    }

    input {
        margin: 10px;
    }

    .rounded {
        height: 50px;
        border-radius: 25px;
    }

    body {
        background-image: url("https://www.ubackground.com/_ph/18/317745804.jpg");
        background-repeat: no-repeat;
        background-attachment: fixed;
    }

    .fade-enter{
        opacity: 0;
    }
    .fade-enter-active{
        transition: opacity 1s;

    }
    .fade-leave{

    }
    .fade-leave-active{
        transition: opacity 1s;
        opacity: 0;
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
            transform: translateX(-20px);
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
            transform: translateX(20px);
        }
    }


</style>
