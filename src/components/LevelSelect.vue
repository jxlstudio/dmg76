<template>
    <select>
        <option v-for="(level, index) in levels" :key="level" :value="getBaseDamage(index)" v-on:input="$emit('input', $event.target.value)">Level {{level}} | Base Dmg: {{getBaseDamage(index)}}</option>
    </select>
</template>

<script>
export default {
  props: ['levels', 'damage'],
  methods: {
    getBaseDamage: function (id) {
      return this.damage[id]
    }
  }
}
</script>
