<template>
    <div id="app">
        <div class="app__post_list">
            <PostCard
                v-for="(v, i) in postList"
                :key="v.id"
                :index="i"
                :url="v.url"
                :eye="v.eye"
                :comments="v.comments"
                :hearts="v.hearts"
                :thumbnailUrl="v.thumbnailUrl"
                :title="v.title"
                @expand="showModal"
            ></PostCard>
        </div>
        <TheModal
            v-if="modal"
            :url="expandImage"
            @collapse="closeModal()"
        ></TheModal>
    </div>
</template>

<script>
import PostCard from './components/PostCard';
import TheModal from './components/TheModal';
import axios from 'axios';

export default {
    name: 'app',
    data () {
        return {
            postList: [],
            modal: false,
            expandImage: ''
        };
    },
    components: {
        PostCard,
        TheModal
    },
    methods: {
        init (response) {
            let rData = (response.data).slice(0, 10);
            this.postList = rData.map(v => {
                let wch = {
                    eye: this.randomNumber(),
                    comments: this.randomNumber(),
                    hearts: this.randomNumber()
                }

                return Object.assign(v, wch);
            });
        },
        randomNumber () {
            return Math.floor(Math.random() * (1500 - 500 + 1) ) + 500;
        },
        showModal (index) {
            this.expandImage = this.postList[index].url;
            this.modal = true;
        },
        closeModal () {
            this.modal = false;
        }
    },
    created () {
        axios
        .get('https://jsonplaceholder.typicode.com/photos')
        .then(this.init);
    }
}
</script>

<style lang="scss">
    body {
        background-color: #f4f4f4;
    }

    #app {
        max-width: 1200px;
        color: #2c3e50;
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;

        .app__post_list {
            display: flex;
            flex-wrap: wrap;
        }
    }
</style>
