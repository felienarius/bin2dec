<template>
  <div class="App">
    <div class="title">
      <h1>Bin2Dec</h1>
    </div>
    <p class="info">
      Enter a <strong>binary</strong> number, get a <strong>decimal</strong> conversion.
    </p>
    <InputBinary
      :value="inputBin.value"
      :isBinary="inputBin.binary"
      @update:value="handleBinaryInput"
    />
    <DisplayDecimal :decNum="decNum" :isBinary="inputBin.binary" />
    <footer>
      Made by
      <a href="https://www.github.com/Felienarius/" target="_blank" rel="noopener noreferrer">
        Felienarius
      </a>
    </footer>
  </div>
</template>

<script>
import InputBinary from './components/InputBinary.vue'
import DisplayDecimal from './components/DisplayDecimal.vue'

export default {
  components: {
    InputBinary,
    DisplayDecimal
  },

  data() {
    return {
      inputBin: {
        value: '',
        binary: false
      },
      decNum: '-'
    }
  },

  watch: {
    'inputBin.value': {
      handler(newVal) {
        if (newVal.length > 0) {
          if (this.inputBin.binary) {
            this.decNum = this.convertToDec(newVal)
          } else {
            this.decNum = "Binary number contains only 0's and 1's (enter 0 or 1)."
          }
        } else {
          this.decNum = '-'
        }
      },
      immediate: true
    }
  },

  methods: {
    handleBinaryInput(value) {
      this.inputBin.value = value
      this.inputBin.binary = !/[^01]/.test(value)
    },

    convertToDec(num) {
      return num
        .split('')
        .reverse()
        .reduce((sum, item, index) => {
          return sum + (item === '1' ? Math.pow(2, index) : 0)
        }, 0)
    }
  }
}
</script>

<style>
/* Resetowanie styli dla tagów HTML */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
  background-color: #f9f9f9;
  color: #333;
}

.App {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  height: 100vh;
  text-align: center;
  font-family: 'Roboto', 'Helvetica', 'Arial', sans-serif;
  font-size: 1rem;
  line-height: 1;
  line-height: 1.5rem;
  background: linear-gradient(-30deg, rgba(0, 0, 0, 0.999), rgba(0, 0, 0, 0.911));
  color: #fff;
}

h1 {
  font-size: 4rem;
  text-align: center;
  margin-bottom: 48px;
  line-height: 1;
}

p {
  font-size: 1.4rem;
  margin-bottom: 20px;
  line-height: 1.2;
}

a {
  color: #7bff7b;
  text-decoration: none;
  font-weight: bold;
}

a:hover {
  text-decoration: underline;
}

footer {
  position: absolute;
  bottom: 1rem;
  font-size: 0.85rem;
  color: #aeaeae;
}
</style>
