<template>
    <li class="list-group-item media" @click="onSelectVideo">
        <img class="mr-3" :src="imgUrl" :alt="video.snippet.title"/>
        <div class="media-body">
            <h6>
                {{video.snippet.title}}
            </h6>
        </div>
    </li>
</template>

<script>
    export default {
        name: 'VideoItem',
        props: ['video'],
        computed: {
            imgUrl() {
                return this.video.snippet.thumbnails.default.url;
            },
        },
        methods: {
            onSelectVideo() {
                this.$emit('selectVideo', this.video);
            }
        }
    }
</script>

<style scoped>
    li {
        display: flex;
        cursor: pointer;
    }

    li:hover {
        background-color: #eeeeee;
    }
</style>