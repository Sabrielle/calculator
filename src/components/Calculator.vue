<template>
  <div class="calculator">
    <div class="calculator-input">
      <p class="input-formula">{{ formula }}</p>
      <input
        class="input"
        type="text"
        maxlength="40"
        v-model="input"
        :class="{ 'small' : input.length > 12 }"
        disabled
      />
    </div>
    <div class="buttons">
      <div class="row">
        <div class="col-1">
          <button class="btn" @click="cleanInput()">AC</button>
        </div>
        <div class="col-1">
          <button class="btn" @click="toggle()">+/-</button>
        </div>
        <div class="col-1">
          <button class="btn" disabled>%</button>
        </div>
        <div class="col-1">
          <button class="btn btn-control" @click="action('/')">/</button>
        </div>
      </div>
      <div class="row">
        <div class="col-1">
          <button class="btn" @click="addDigit('7')">7</button>
        </div>
        <div class="col-1">
          <button class="btn" @click="addDigit('8')">8</button>
        </div>
        <div class="col-1">
          <button class="btn" @click="addDigit('9')">9</button>
        </div>
        <div class="col-1">
          <button class="btn btn-control" @click="action('*')">x</button>
        </div>
      </div>
      <div class="row">
        <div class="col-1">
          <button class="btn" @click="addDigit('4')">4</button>
        </div>
        <div class="col-1">
          <button class="btn" @click="addDigit('5')">5</button>
        </div>
        <div class="col-1">
          <button class="btn" @click="addDigit('6')">6</button>
        </div>
        <div class="col-1">
          <button class="btn btn-control" @click="action('-')">-</button>
        </div>
      </div>
      <div class="row">
        <div class="col-1">
          <button class="btn" @click="addDigit('1')">1</button>
        </div>
        <div class="col-1">
          <button class="btn" @click="addDigit('2')">2</button>
        </div>
        <div class="col-1">
          <button class="btn" @click="addDigit('3')">3</button>
        </div>
        <div class="col-1">
          <button class="btn btn-control" @click="action('+')">+</button>
        </div>
      </div>
      <div class="row">
        <div class="col-2">
          <button class="btn" @click="addDigit(0)">0</button>
        </div>
        <div class="col-1">
          <button class="btn" @click="addDigit('.')" :disabled="!hasDot">,</button>
        </div>
        <div class="col-1">
          <button class="btn btn-control" @click="calculate()">=</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data: function() {
    return {
      input: 0,
      formula: ""
    };
  },
  computed: {
    hasDot: function () {
      return String(this.input).indexOf(".") === -1
    }
  },
  methods: {
    addDigit: function(digit) {
      return this.input === 0 && digit !== "."
        ? (this.input = digit)
        : (this.input += digit);
    },
    action: function(action) {
      if (this.formula.length) {
        this.calculate();
        this.formula = this.input;
      } else {
        this.formula += this.input;
      }
      this.formula += action;
      this.input = 0;
    },
    calculate: function() {
      this.formula += this.input;
      this.input = eval(this.formula);
      this.formula = "";
    },
    cleanInput: function() {
      if (this.input === 0) {
        this.formula = "";
      } else {
        this.input = 0;
      }
    },
    toggle: function() {
      return (this.input = this.input * -1);
    }
  }
};
</script>

<style scoped>
.calculator {
  width: 100%;
  margin: 0 auto;
  display: flex;
  padding: 0;
  max-width: 400px;
  flex-direction: column;
}
.calculator-input {
  padding: 30px;
  background: #4c4c4c;
}
.input {
  color: #cccccc;
  outline: none;
  width: 100%;
  border: none;
  display: block;
  font-size: 40px;
  background: none;
  text-align: right;
  font-weight: 300;
  height: 40px;
}
.small {
  font-size: 24px;
}
.input-formula {
  height: 20px;
  font-size: 18px;
  color: #cccccc;
  text-align: right;
}
.row {
  display: flex;
  padding: 0;
  justify-content: space-around;
}
.col-1 {
  flex: 1;
}
.col-2 {
  flex: 2;
}
.btn {
  width: 100%;
  border: none;
  outline: none;
  cursor: pointer;
  background: #d6d6d6;
  border: 1px solid #aaaaaa;
  padding: 15px;
  font-size: 28px;
  color: #000000;
}
.btn:active {
  background: #d0d0d0;
}
.btn:disabled {
  background: #a0a0a0;
  cursor: initial;
}
.btn-control {
  background: #ff9900;
  color: #ffffff;
}
.btn-control:active {
  background: #ffaa22;
}
</style>
