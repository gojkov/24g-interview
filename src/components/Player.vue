<template>

    <div class="container-large">
        <div class="video-player"> 
            <h3>{{ this.activeVideo.title }}</h3>
            <div class="video-container">
                <div class="core-area">
                    <video
                        id="selected-video"
                        controls
                        @ended="addView"
                        width="640" 
                        height="360" 
                        :src="this.activeVideo.videoUrl" 
                        frameborder="0" 
                        allow="encrypted-media" 
                        allowfullscreen
                    ></video>

                    <div class="video-stats">
                        <h6>{{ this.activeVideo.views }} views</h6>

                        <div class="feedback">
                            <div class="like-count">
                                <img @click="addLike" src="../assets/svg/thumbs_up.svg" alt="Likes" id="likeBtn">
                                <span> {{ this.activeVideo.likes }}</span>
                            </div>

                            <div class="dislike-count">
                                <img @click="addDislike" src="../assets/svg/thumbs_down.svg" alt="Dislikes" id="dislikeBtn">
                                <span> {{ this.activeVideo.dislikes }}</span>
                            </div>
                        </div>
                    </div>

                    <div class="accent-line" />
                </div>
                
                <div class="video-list">
                    <div 
                        @click="chooseVideo(video)" 
                        :key="video.id" 
                        v-for="video in videos"
                        class="thumbnail">

                    <div class="thumbnail-img">
                        <img 
                            :src="video.thumbnail"
                             />
                    </div>
                </div>
               </div>
            </div>
            <Footer />
        </div>
    </div>

</template>

<script>
import Vue from 'vue';
import videos from '../videoList';
import Footer from './Footer';
import VueCookies from 'vue-cookies';
//import JQuery from 'jquery';

Vue.use(VueCookies);
VueCookies.config('90d');
//let $ = JQuery

export default {
    name: 'Player',
    components: {
        Footer
    },
    data () {
        return {
            videos,
            activeVideo: videos[0]
        }
    },
    methods: {
        addView() {
            //INCREASE THE VIDEOS VIEWS BY 1 IF COMPLETE
            this.activeVideo.views += 1;
            //SET COOKIE FOR VIEWS PER VIDEO
            this.$cookies.set(this.activeVideo.title, this.activeVideo.views);
        },
        chooseVideo(video){
            //SET VIDEO AS ACTIVE VIDEO
            this.activeVideo = video;
        },
        addLike(){
            //INCREASE LIKES BY 1 ON CLICK
            this.activeVideo.likes +=1;
            //SET COOKIE FOR LIKES PER VIDEO
            this.$cookies.set(this.activeVideo.id, this.activeVideo.likes);
        },
        addDislike(){
            //INCREASE DISLIKES BY 1 ON CLICK 
            this.activeVideo.dislikes +=1;
            //SET COOKIE FOR DISLIKES PER VIDEO
            this.$cookies.set(this.activeVideo.altId, this.activeVideo.dislikes);
        }
    }
}

</script>

<style lang="scss">

.container-large {
    display: block;
    width: 100%;

    .video-player {
        display: inline-block;
        margin: 2.5rem 0 1rem 4rem;

        h3 {
            font-family: 'Brandon Grotesque Medium';
            font-size: 1.2rem;
            letter-spacing: .04em;
            color: $gray-midnight;
        }

        .video-container {
            display: flex;
            flex-direction: row;
            padding-top: .5rem;

            .core-area {
                width: 640px;

                .orangeBorder {
                    border: 4px solid $orange-light;
                }

                .no-border {
                    border: none;
                }
                
                .video-stats {
                    display: flex;
                    flex-direction: row;
                    vertical-align: baseline;
                    justify-content: space-between;
                    font-family: 'Brandon Grotesque Regular';
                    margin-top: .4rem;
                    font-size: 1.7rem;

                    img {
                        width: 1.15rem;
                    }

                    span {
                        font-size: 1.1rem;
                        color: $orange-dark;
                        font-weight: bold;
                    }

                    .feedback {
                        display: flex;
                        font-size: 2rem;
                        justify-content: space-between;
                        width: 100px;
                        vertical-align: baseline;

                        span {
                            padding-left: .4rem;
                        }

                        .like-count,
                        .dislike-count {
                            display: flex;
                            font-size: 1.5rem;
                        }
                    }
                }
                
                .accent-line {
                    height: 1rem;
                    width: 640px;
                    border-bottom: 2px solid rgba(0,0,0,0.1);
                    margin-bottom: .2rem;
                }
            }

            .video-list {
                display: inline-flex;
                flex-direction: column;
                justify-content: space-between;
                margin-left: 2.5rem;
                height: 364px;

                .thumbnail {
                    display: flex;

                    img {
                        width: 168px;
                    }

                }
            }
        }
    }
}

</style>