<script setup>
import TimerItem from './components/TimerItem.vue';
import { ref } from 'vue';
const items = ref(3);
</script>

<template>
  <div class="container">
    <TimerItem v-for="item,i  in items" :key="i" />
    <div class="add-item">
        <button class="add-item__btn"  @click="items++">
            <ion-icon name="add-sharp"></ion-icon>
        </button>
    </div>
  </div>
</template>

<style lang="sass" scoped>
.container
  display: flex
  flex-direction: column
  flex-wrap: wrap
  row-gap: 45px
  column-gap: 50px
  justify-content: center
  align-content: center
  align-items: center
  padding-block: 72px
  @media screen and (min-width: 768px)
    flex-direction: row
.add-item
    width: 225px
    height: 120px
    display: flex
    flex-direction: column
    justify-content: center
    background-color: #696969
    text-align: center
    color: #9E9E9E
    &__btn
      font-size: 30px
</style>

