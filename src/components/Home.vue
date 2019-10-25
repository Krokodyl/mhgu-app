<template>
  <div class="hello">
    <Monsters :monsters="mhdb.monsters"/>
  </div>
</template>

<script>
import mhdb from '../data/monsters2.json';
import Monsters from './Monsters';
export default {
  name: 'Home',
  props: {
    msg: String
  },
  components: {
    Monsters
  },
  data() {
    return {
      mhdb
    }
  }
}
</script>