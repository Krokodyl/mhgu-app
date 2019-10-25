<template>
  <div class="m-div m-panel">
    <table class="m-table m-panel"
      v-for="(weaknesses, mode) in monster.weaknesses"
      :key="mode"
    >
      <thead>
        <tr>
          <th colspan="10">
            {{ monster.name }}
          </th>
        </tr>
        <tr>
          <th colspan="10">
            <span v-if="mode == 'Normal'"><br/></span>
            <span v-if="mode != 'Normal'">({{ mode }})</span>
          </th>
        </tr>
      </thead>
      <tr>
        <td rowspan="3">
          <img v-bind:src="getImgUrl('icons/' + monster.icon + '.png')" width="50" />
        </td>
        <td>{{ monster.hp }}</td>
      </tr>
      <tr>
        <td>
          <!--span  v-for="(ailment) in monster.ailments" :key="ailment" >{{ ailment }}</span-->
          <img v-for="(ailment) in monster.ailments" :key="ailment" :src="getImgUrl('icons/ailments/' + ailment + '.png')" width="15" />
        </td>
      </tr>
      <tr>
        <td><!--img v-for="n in [1,2,3,4,5]" :key="n" :src="monster.weaknesses[mode][n]"/></td-->
        <table>
          <tr v-for="n in [0,1,2,3,4,5,6,7]" :key="n" :value="n">
            <!--td v-for="w in n" :key="w">
              {{ getWeaknessVal(monster,mode,n) }}
            </td-->
            <td>
              <Element :element="n" :value="Number(monster.weaknesses[mode][n])"/>
            </td>
          </tr>
          <tr>
            <td>
              <Item v-for="n in [8,9,10,11,12,13]" :key="n" :element="n" :value="Number(monster.weaknesses[mode][n])" />
            </td>
          </tr>
        </table>
        </td>
        <!--img v-for="n in [0,1,2,3,4]" :key="n" :src="getWeaknessIcon(n)" width="20"/></td-->
      </tr>
      <tr>
        <td>items</td>
      </tr>
    </table>
  </div>
</template>

<script>
import Element from './Element.vue';
import Item from './Item.vue';
export default {
  name: "Monster",
  props: {
    monster: Object
  },
  methods: {
    getImgUrl(pic) {
      try {
        return require("../assets/" + pic);
      } catch (error) {
        //console.log('No asset found for '+pic);
      }
    },
    getWeaknessIcon(n) {
      switch(n) {
        case 0:return this.getImgUrl('icons/element_fire.png');
        case 1:return this.getImgUrl('icons/element_water.png');
        case 2:return this.getImgUrl('icons/element_thunder.png');
        case 3:return this.getImgUrl('icons/element_ice.png');
        case 4:return this.getImgUrl('icons/element_dragon.png');
      }
    },
    getWeaknessVal(monster, mode, n) {
      return monster.weaknesses[mode][n];
    }
  },
  components: {
    Element,
    Item
  }
};
</script>