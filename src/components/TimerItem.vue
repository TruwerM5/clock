<script setup>
import { ref } from 'vue';
const state = ref('pause');

const seconds = ref(0);
const minutes = ref(0);
const hours = ref(0);
let interval;
function startTimer() {
    state.value = 'play';
    interval = setInterval(() => {
        seconds.value++;
        if(seconds.value == 60) {
            seconds.value = 0;
            minutes.value++;
        }
        
        if(minutes.value == 60) {
            minutes.value = 0;
            seconds.value = 0;
            hours.value++;
        }
    }, 1000)
}

function pause() {
    state.value = 'pause';
    clearInterval(interval);
}

function stop() {
    seconds.value = 0;
    minutes.value = 0;
    hours.value = 0;
    clearInterval(interval);
    state.value = 'pause';
}

</script>

<template>
    <div :class="['timer', state === 'play' ? 'active' : '']">
        <div class="timer__top">
            <span 
            class="timer__time">
                {{ hours }}:
            </span>
            <span 
            class="timer__time">
                {{ minutes }}:
            </span>
            <span
            class="timer__time">
                {{ seconds }}
            </span>
        </div>
        <div class="timer__bottom">
            <button v-if="state === 'pause'" @click="startTimer" class="timer__btn">
                <ion-icon name="play-sharp" class="icon"></ion-icon>
            </button>
            <button v-else-if="state === 'play'" @click="pause" class="timer__btn">
                <ion-icon name="pause-sharp" class="icon"></ion-icon>
            </button>
            <button @click="stop" class="timer__btn">
                <ion-icon name="stop-sharp" class="icon"></ion-icon>
            </button>
        </div>
    </div>
</template>

<style lang="sass" scoped>
.timer
    width: 225px
    height: 120px
    display: flex
    flex-direction: column
    justify-content: center
    background-color: #696969
    text-align: center
    color: #9E9E9E
    &.active
      color: #FFF  
      .icon
        color: #FFF
    .icon
        color: #9E9E9E
        font-size: 25px
    &__top
        padding: 20px
        border-bottom: 1px solid #FFF
        font-size: 22px
    &__bottom
        padding: 20px
    &__btn
        margin-inline: 24px

</style>