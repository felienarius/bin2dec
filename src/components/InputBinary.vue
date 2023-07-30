<template>
  <div class="input">
    <input
      :class="{ alert: !isBinary }"
      type="text"
      :value="value"
      minlength="1"
      maxlength="16"
      @input="handleBinaryInput"
    />
  </div>
</template>

<script>
export default {
  props: ['value', 'isBinary'],
  methods: {
    handleBinaryInput(e) {
      const value = e.target.value
      this.$emit('update:value', value)
    }
  }
}
</script>

<style scoped>
input {
  min-width: 320px;
  width: 100%;
  max-width: 80%;
  padding: 0.75rem 1rem;
  font-family: 'Roboto Mono', 'Consolas', monospace;
  font-size: 2rem;
  color: #fff;
  background: none;
  border: 1px solid #fff;
  outline: 0;
}

input:focus {
  border-color: rgb(167, 255, 165);
}
input.alert:focus {
  border-color: #ff7b7b;
}
</style>
