<template>
  <label>How would you rate your experience here?</label>
  <ul>
    <li :class="{ active: modelValue === 'poor' }"><button type='button' @click="activate('poor')">Poor</button></li>
    <li :class="{ active: modelValue === 'average' }"><button type='button'
        @click="activate('average')">Average</button></li>
    <li :class="{ active: modelValue === 'excellent' }"><button type='button'
        @click="activate('excellent')">Excellent</button></li>
  </ul>
</template>

<script>
export default {
  props: ['modelValue'],
  emits: ['update:modelValue'],
  methods: {
    activate(option) {
      this.$emit('update:modelValue', option);
    }
  }
}
</script>

<style scoped>
label {
  display: flex;
  margin: 1rem 0;
  font-weight: 700;
}

.active {
  border-color: blue;
  background-color: rgb(237, 237, 252);
}

.active button {
  color: blue;
}

ul {
  list-style: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
  gap: 1rem;
}

li {
  border: 1px solid #ccc;
  padding: 0.5rem 1rem;
  display: flex;
  justify-content: center;
  border-radius: 5px;
  align-items: center;
}

button {
  font-style: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
</style>