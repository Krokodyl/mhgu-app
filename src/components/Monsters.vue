<template>
  <div class="hello">
    <Monster v-for="item in monsters" :key="item.id" :monster="item"/>
  </div>
</template>

<script>
import Monster from './Monster.vue';
export default {
  name: 'Monsters',
  props: {
    monsters: Array
  },
  components: {
    Monster
  }
}
</script>