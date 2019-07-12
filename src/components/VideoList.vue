<template>
    <ul class="list-group col-md-4">
        <VideoItem v-for="video in videos"
                   :video="video"
                   :key="video.id.videoId"
                   @selectVideo="onSelectVideo" />
    </ul>
</template>

<script>
    import VideoItem from './VideoItem';

    export default {
        name: 'VideoList',
        components: {
            VideoItem
        },
        props: {
            videos: Array
        },
        methods: {
            onSelectVideo(video) {
                this.$emit('selectVideo', video);
            }
        }
    }
</script>

<style>

</style>