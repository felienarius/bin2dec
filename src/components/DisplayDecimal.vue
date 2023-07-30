<template>
  <div>
    <h2 :class="{ error: !isBinary && decNum !== '-', success: isBinary && decNum !== '-' }">
      Decimal Number:
    </h2>
    <p>{{ decNum }}</p>
  </div>
</template>

<script>
export default {
  props: ['decNum', 'isBinary']
}
</script>

<style scoped>
h2 {
  display: block;
  margin: 20px 0;
  font-size: 1.4rem;
}
h2.error {
  color: #ff7b7b;
}
h2.success {
  color: #7bff7b;
}
h2.success + p {
  font-size: 2.5rem;
  letter-spacing: 0.2rem;
}
</style>
