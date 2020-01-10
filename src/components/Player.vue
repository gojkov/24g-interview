<template>
    <b-container fluid class="container-large">
        <b-container fluid class="video-player"> 
            <h3>{{ this.activeVideo.title }}</h3>
            <b-container fluid class="video-container">
                <b-container fluid class="core-area">
                    <b-embed type="video" aspect="16by9">
                        <video
                            id="selected-video"
                            controls
                            width="640"
                            height="360"
                            @ended="addView" 
                            :src="this.activeVideo.videoUrl" 
                            frameborder="0" 
                            allow="encrypted-media" 
                            allowfullscreen
                        ></video>
                    </b-embed>
                            
                    <b-container tag="div" fluid class="video-stats">
                        <h6>{{ this.activeVideo.views }} views</h6>

                        <b-container fluid class="feedback">
                            <div class="like-count">
                                <img @click="addLike" src="../assets/svg/thumbs_up.svg" alt="Likes" id="likeBtn">
                                <span> {{ this.activeVideo.likes }}</span>
                            </div>

                            <div class="dislike-count">
                                <img @click="addDislike" src="../assets/svg/thumbs_down.svg" alt="Dislikes" id="dislikeBtn">
                                <span> {{ this.activeVideo.dislikes }}</span>
                            </div>
                        </b-container>
                    </b-container>  
            
                    <div fluid class="accent-line" />
                </b-container>
                        <div class="video-list">
                            <div 
                                @click="chooseVideo(video)" 
                                v-for="video in videos"
                                :key="video.id"
                                class="thumbnail">

                                <div class="thumbnail-img">
                                    <img
                                    :style="[video === activeVideo ? {border: '4px solid #FAA61A'} : {padding: '2px'}]"
                                    :src="video.thumbnail"
                                    />
                                </div>  
                            </div>                   
                    </div>  
            </b-container>

            <Footer />

        </b-container>
    </b-container>
</template>

<script>
import Vue from 'vue'
import videos from '../videoList'
import Footer from './Footer'
import VueCookies from 'vue-cookies'

Vue.use(VueCookies)

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
            //INCREASE VIEWS BY 1 ON CLICK
            this.activeVideo.views++
            //SET COOKIE FOR VIEWS PER VIDEO
            this.$cookies.set(this.activeVideo.title, this.activeVideo.views, '30d', '/')
            //REFLECT VIEWS UPDATE
            this.activeVideo.views == Number(this.$cookies.get(this.activeVideo.title))
        },
        chooseVideo(video){
            //SET VIDEO AS ACTIVE VIDEO
            this.activeVideo = video
            //GET COOKIE VALUES AND REFLECT IN VIEWS, LIKES, DISLIKES
            video.views = Number(this.$cookies.get(this.activeVideo.title))
            video.likes = Number(this.$cookies.get(this.activeVideo.id))
            video.dislikes = Number(this.$cookies.get(this.activeVideo.altId))
        },
        addLike(){
            //INCREASE LIKES BY 1 ON CLICK
            this.activeVideo.likes++
            //SET COOKIE FOR LIKES PER VIDEO
            this.$cookies.set(this.activeVideo.id, this.activeVideo.likes, '30d', '/')
            //REFLECT LIKES UPDATE
            this.activeVideo.likes == Number(this.$cookies.get(this.activeVideo.id))
        },
        addDislike(){
            //INCREASE DISLIKES BY 1 ON CLICK 
            this.activeVideo.dislikes++
            //SET COOKIE FOR DISLIKES PER VIDEO
            this.$cookies.set(this.activeVideo.altId, this.activeVideo.dislikes, '30d', '/')
            //REFLECT DISLIKES UPDATE
            this.activeVideo.dislikes == Number(this.$cookies.get(this.activeVideo.altId))
        },
        showStats(){
            // GATHER USER STATS FOR APP MOUNT
            this.activeVideo.views = Number(this.$cookies.get(this.activeVideo.title))
            this.activeVideo.likes = Number(this.$cookies.get(this.activeVideo.id))
            this.activeVideo.dislikes = Number(this.$cookies.get(this.activeVideo.altId))
        }
    },
    mounted() {
        // MOUNT EXISTING STATS
        this.showStats()
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
            font-weight: 600;
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
                
                .video-stats {
                    display: flex;
                    flex-direction: row;
                    vertical-align: baseline;
                    justify-content: space-between;
                    font-family: 'Brandon Grotesque Medium';
                    margin-top: .4rem;
                    font-size: 1.7rem;

                    h6 {
                        margin-top: .5rem;
                        font-weight: 600;
                    }

                    img {
                        width: .9rem;
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
                            font-size: 1rem;
                            padding-left: .4rem;
                            padding-top: .4rem;
                        }

                        .like-count,
                        .dislike-count {
                            display: flex;
                            font-size: 1rem;
                        }

                        #likeBtn,
                        #dislikeBtn {

                            &:hover {
                                transform: scale(1.2);
                                transition: all .2s;
                            }
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
                height: 362px;
                width: 168px;

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