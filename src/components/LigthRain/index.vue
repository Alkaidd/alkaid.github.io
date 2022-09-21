<template>
<div v-if="showAnime" class="g-box-ani">
    <div class="g-scroll" id="g-scroll"></div>
    <div class="g-wrap">
        <div class="g-container">
            <div class="g-lightrain">
                <MyRain/>
            </div>
            <div class="g-blood"></div>
        </div>
    </div>
</div>
</template>

<script>
import MyRain from './components/MyRain.vue'
import { throttle } from '@/jsTool/myLodash'

export default {
    name: 'LightRain',
    components: {
        MyRain
    },
    created() {
        this.showAnime = true;
        this.animeLoad = this.throttle(this.destoryAnime,200);
        document.addEventListener('scroll', this.animeLoad);
    },
    beforeDestroy() {
        console.log('des');
        this.throttle = null;
    },
    data() {
        return {
            showAnime: true,
            throttle,
            animeLoad:'',
        }
    },
    methods: {
        destoryAnime() {
            const windowHeight = document.documentElement.clientHeight;
            const scrollHeight = document.documentElement.scrollTop;
            const documentHeight = document.documentElement.offsetHeight;

            let isBottom = (windowHeight+scrollHeight) >= (documentHeight-200);
            if(isBottom) {
                console.log('触底了');
                this.showAnime = false;
                document.removeEventListener('scroll', this.animeLoad);
            }
        }
    }
}
</script>

<style>
.g-scroll {
    position: relative;
    width: 100%;
    height: 300vh;
}
.g-wrap {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    overflow: hidden;
}
.g-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    animation-name: scale;
    animation-duration: 10s;
    animation-timeline: box-move;
}
.g-lightrain {
    position: absolute;
    width: 100%;
    height: 100%;
    background: black;
    mask: url(@/assets/blood.svg), linear-gradient(#fff, #fff);
    mask-repeat: no-repeat;
    mask-position: center center;
    -webkit-mask-composite: xor;
    mask-composite: xor;
    z-index: 1;
}
.g-blood {
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: white;
    mask: url(@/assets/blood.svg);
    mask-repeat: no-repeat;
    mask-position: center center;
    z-index: 3;
    animation-name: reOpacityChange;
    animation-duration: 10s;
    animation-timeline: box-move;
}
@keyframes reOpacityChange {
    0% {
        opacity: 1;
    }
    100% {
        opacity: 0;
    }
}
@scroll-timeline box-move {
    source: selector("#g-scroll");
    orientation: "vertical";
}
@keyframes scale {
    0% {
        transform: scale(1);
    }
    100% {
        transform: scale(60);
    }
}

@supports not (animation-timeline: box-move) {
    .g-scroll {
        position: relative;
        width: 100%;
        height: 100%;
    }
    .g-container {
        position: absolute;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        animation-name: reOpacityChange;
        animation-duration: 10s;
        animation-iteration-count: 1;
    }
    .g-blood {
        position: absolute;
        width: 100%;
        height: 100%;
        background-color: white;
        mask: url(@/assets/blood.svg);
        mask-repeat: no-repeat;
        mask-position: center center;
        z-index: 3;
        animation-name: reOpacityChange;
        animation-duration: 10s;
        animation-iteration-count: 1;
    }
}
</style>