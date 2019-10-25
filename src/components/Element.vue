<template>
  <div>
    <!--span>el={{ element }} val={{ value }}</span-->
    <img
      v-for="n in 8"
      :key="n"
      :src="getWeaknessIcon(element)"
      width="15"
      :alt="getWeaknessName(element)"
      :title="getWeaknessName(element)"
      :class="getWeaknessStyleClass(n, value)"
    />
    <!--img v-for="n in [0,1,2,3,4]" :key="n" :src="getWeaknessIcon(n)" width="20"/></td-->
  </div>
</template>

<script>
export default {
  name: "Element",
  props: {
    element: Number,
    value: Number
  },
  methods: {
    getImgUrl(pic) {
      try {
        return require("../assets/" + pic);
      } catch (error) {
        //console.log('No asset found for '+pic);
      }
    },
    getWeaknessName(n) {
      switch (n) {
        case 0:
          return 'Fire';
        case 1:
          return 'Water';
        case 2:
          return 'Thunder';
        case 3:
          return 'Ice';
        case 4:
          return 'Dragon';
        case 5:
          return 'Poison';
        case 6:
          return 'Paralysis';
        case 7:
          return 'Sleep';
      }
    },
    getWeaknessIcon(n) {
      switch (n) {
        case 0:
          return this.getImgUrl("icons/element_fire.png");
        case 1:
          return this.getImgUrl("icons/element_water.png");
        case 2:
          return this.getImgUrl("icons/element_thunder.png");
        case 3:
          return this.getImgUrl("icons/element_ice.png");
        case 4:
          return this.getImgUrl("icons/element_dragon.png");
        case 5:
          return this.getImgUrl("icons/status_poison.png");
        case 6:
          return this.getImgUrl("icons/status_paralysis.png");
        case 7:
          return this.getImgUrl("icons/status_sleep.png");
      }
    },
    getWeaknessStyleClass(n, value) {
      if (n <= value) return "opaque";
      else return "transparent";
    },
    getWeaknessVal(monster, mode, n) {
      return monster.weaknesses[mode][n];
    }
  }
};
</script>