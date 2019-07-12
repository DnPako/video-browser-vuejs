<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"/>
        <div class="row">
            <VideoDetail :video="selectedVideo"/>
            <VideoList :videos="videos" @selectVideo="onVideoSelect"/>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';
    import SearchBar from './components/SearchBar';
    import VideoList from './components/VideoList';
    import VideoDetail from './components/VideoDetail';
    import Keys from './Secrets/Keys';

    const {API_KEY} = Keys;

    export default {
        name: 'App',
        components: {
            SearchBar,
            VideoList,
            VideoDetail
        },
        data() {
            return {
                videos: [],
                selectedVideo: null
            }
        },
        methods: {
            async onTermChange(value) {
                const response = await axios.get('https://www.googleapis.com/youtube/v3/search', {
                    params: {
                        key: API_KEY,
                        type: 'video',
                        part: 'snippet',
                        q: value
                    }
                });

                this.videos = [...response.data.items];

            },
            onVideoSelect(video) {
                this.selectedVideo = video;
                console.log(this.selectedVideo);

            }
        }
    };
</script>