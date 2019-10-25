<template>
  <div style="display:inline-block;margin:2px;">
    <!--span>el={{ element }} val={{ value }}</span-->
    <img
      :src="getIcon(element)"
      width="15"
      :alt="getName(element)"
      :title="getName(element)"
      :class="getStyleClass(value)"
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
    getName(n) {
      switch (n) {
        case 8:
          return 'Pitfall Trap';
        case 9:
          return 'Shock Trap';
        case 10:
          return 'Flash Bomb';
        case 11:
          return 'Sonic Bomb';
        case 12:
          return 'Dung Bomb';
        case 13:
          return 'Meat';
      }
    },
    getIcon(n) {
      switch (n) {
        case 8:
          return this.getImgUrl("icons/item_trap_pitfall.png");
        case 9:
          return this.getImgUrl("icons/item_trap_shock.png");
        case 10:
          return this.getImgUrl("icons/item_bomb_flash.png");
        case 11:
          return this.getImgUrl("icons/item_bomb_sonic.png");
        case 12:
          return this.getImgUrl("icons/item_bomb_dung.png");
        case 13:
          return this.getImgUrl("icons/item_meat.png");
      }
    },
    getStyleClass(value) {
      if (value==1) return "opaque";
      else return "transparent";
    },
    getVal(monster, mode, n) {
      return monster.weaknesses[mode][n];
    }
  }
};
</script>