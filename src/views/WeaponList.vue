<template>
  <div>
    <table>
      <tr>
        <th>Name</th>
        <th>Base Damage</th>
        <th>Bloodied</th>
      </tr>
      <tr v-for="weapon in ranged" :key="weapon.name">
        <td>{{ weapon.name }}</td>
        <!-- <td><LevelSelect :levels="weapon.level" :damage="weapon.damage" v-model="baseDmg"/></td> -->
        <td>
          <ul>
              <li v-for="(lvl, index) in weapon.level" :key="lvl">Level {{lvl}} - Dmg: {{weapon.damage[index]}}</li>
          </ul>
        </td>
        <td>{{ baseDmg }}</td>
      </tr>
      <tr v-for="weapon in melee" :key="weapon.name">
        <td>{{ weapon.name }}</td>
        <td>{{ weapon.level }}<br>{{ weapon.damage }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import ranged from '@/assets/ranged.json'
import rangedEffects from '@/assets/ranged-effects.json'
import melee from '@/assets/melee.json'
import meleeEffects from '@/assets/melee-effects.json'
// import LevelSelect from '@/components/LevelSelect.vue'

export default {
  name: 'WeaponList',
  components: {
    // LevelSelect
  },
  data () {
    return {
      ranged: ranged.data,
      rangedEffects: rangedEffects.data,
      melee: melee.data,
      meleeEffects: meleeEffects.data,
      baseDmg: null
    }
  },
  methods: {
    getBaseDamage: function (id) {
      return this.damage[id]
    }
  }
}
</script>
