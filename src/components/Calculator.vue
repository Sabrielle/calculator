<template>
  <div class="calculator">
    <div class="calculator-input">
      <input class="input" type="text"/>
    </div>
    <div class="buttons">
      <div class="row">
        <div class="col-1">
          <button class="btn">AC</button>
        </div>
        <div class="col-1">
          <button class="btn">+/-</button>
        </div>
        <div class="col-1">
          <button class="btn" disabled>%</button>
        </div>
        <div class="col-1">
          <button class="btn btn-control">/</button>
        </div>
      </div>
      <div class="row">
        <div class="col-1">
          <button class="btn">7</button>
        </div>
        <div class="col-1">
          <button class="btn">8</button>
        </div>
        <div class="col-1">
          <button class="btn">9</button>
        </div>
        <div class="col-1">
          <button class="btn btn-control">x</button>
        </div>
      </div>
      <div class="row">
        <div class="col-1">
          <button class="btn">4</button>
        </div>
        <div class="col-1">
          <button class="btn">5</button>
        </div>
        <div class="col-1">
          <button class="btn">6</button>
        </div>
        <div class="col-1">
          <button class="btn btn-control">-</button>
        </div>
      </div>
      <div class="row">
        <div class="col-1">
          <button class="btn">1</button>
        </div>
        <div class="col-1">
          <button class="btn">2</button>
        </div>
        <div class="col-1">
          <button class="btn">3</button>
        </div>
        <div class="col-1">
          <button class="btn btn-control">+</button>
        </div>
      </div>
      <div class="row">
        <div class="col-2">
          <button class="btn">0</button>
        </div>
        <div class="col-1">
          <button class="btn">,</button>
        </div>
        <div class="col-1">
          <button class="btn btn-control">=</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Calculator'
}
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
  background: #4C4C4C;
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
  background: #D6D6D6;
  border: 1px solid #AAAAAA;
  padding: 15px;
  font-size: 28px;
  color: #000000;
}
.btn:active {
  background: #D0D0D0;
}
.btn:disabled {
  background: #A0A0A0;
  cursor: initial;
}
.btn-control {
  background: #FF9900;
  color: #ffffff;
}
.btn-control:active {
  background: #FFAA22;
}
</style>
