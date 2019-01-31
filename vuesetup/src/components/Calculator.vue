<template>
  <div class="calculator">
    <div class="result">{{ resultValue }}</div>
    <div class="btn clear" @click="clear">C</div>
    <div class="btn operator" @click="handleOp('/')">/</div>
    <div class="btn" @click="handleNum(7)">7</div>
    <div class="btn" @click="handleNum(8)">8</div>
    <div class="btn" @click="handleNum(9)">9</div>
    <div class="btn operator" @click="handleOp('*')">*</div>
    <div class="btn" @click="handleNum(4)">4</div>
    <div class="btn" @click="handleNum(5)">5</div>
    <div class="btn" @click="handleNum(6)">6</div>
    <div class="btn operator" @click="handleOp('-')">-</div>
    <div class="btn" @click="handleNum(1)">1</div>
    <div class="btn" @click="handleNum(2)">2</div>
    <div class="btn" @click="handleNum(3)">3</div>
    <div class="btn operator" @click="handleOp('+')">+</div>
    <div class="btn zero" @click="handleNum(0)">0</div>
    <div class="btn operator" @click="handleOp('=')">=</div>
  </div>
</template>

<script>
export default {
  name: 'Calculator',
  data () {
    return {
      savedValue: false,
      current: '0',
      currentOperator: false
    }
  },
  methods: {
    clear () {
      this.savedValue = false
      this.current = '0'
      this.currentOperator = false
    },
    handleNum (n) {
      if (this.currentOperator === '=') {
        this.savedValue = false
      }
      this.current = this.current * 10 + n
    },
    handleOp (str) {
      if (this.currentOperator) {
        this.calc()
      } else {
        this.savedValue = this.current
      }
      this.current = 0
      this.currentOperator = str
    },
    calc () {
      if (this.currentOperator === '+') {
        this.savedValue += this.current
      } else if (this.currentOperator === '-') {
        this.savedValue -= this.current
      } else if (this.currentOperator === '*') {
        this.savedValue *= this.current
      } else if (this.currentOperator === '/') {
        this.savedValue /= this.current
      } else if (this.currentOperator === '=' && this.current) {
        this.savedValue = this.current
      }
    }
  },
  computed: {
    resultValue () {
      return this.savedValue
        ? this.current ? this.current : this.savedValue
        : this.current
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  .calculator {
    display: grid;
    grid-template-columns: repeat(4, minmax(60px, 1fr));
    max-width: 500px;
    margin: auto;
    padding: 10px;
    border: 1px solid grey;
    font-size: 20px;
    font-weight: 700;
  }

  .result {
    grid-column: 1 / 5;
    text-align: right;
  }

  .result,
  .btn {
    margin: 5px;
    padding: 10px;
    background-color: lightgrey;
    border: 1px solid grey;
    border-radius: 2px;
  }

  .btn {
    cursor: pointer;
  }

  .operator {
    background-color: #ffe87c;
  }

  .clear,
  .zero {
    grid-column: 1 / 4;
  }

  .clear {
    background-color: #528CE0;
  }
</style>
