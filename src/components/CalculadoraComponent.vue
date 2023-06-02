<template>
  <div class="calculator">
    <h1>{{ msg }}</h1>

    <div class="container">
    <div class="display">{{ output || 0 }}</div>
    <div class="container-mg">
      <div class="buttons">
        <div class="row">
          <div @click="clearField" class="button clear right">AC</div>
          <div class="button operator right">+/-</div>
          <div @click="calculatePercent" class="button operator right">%</div>
          <div class="button operator">/</div>
        </div>
        <div class="row">
          <div @click="updateOutput(7)" class="button">7</div>
          <div @click="updateOutput(8)" class="button">8</div>
          <div @click="updateOutput(9)" class="button">9</div>
          <div class="button operator">×</div>
        </div>
        <div class="row">
          <div @click="updateOutput(4)" class="button">4</div>
          <div @click="updateOutput(5)" class="button">5</div>
          <div @click="updateOutput(6)" class="button">6</div>
          <div class="button operator">-</div>
        </div>
        <div class="row">
          <div @click="updateOutput(1)" class="button">1</div>
          <div @click="updateOutput(2)" class="button">2</div>
          <div @click="updateOutput(3)" class="button">3</div>
          <div class="button operator">+</div>
        </div>
        <div class="row">
          <div @click="updateOutput(0)" class="button double">0</div>
          <div @click="updateOutput('.')" class="button">.</div>
          <div @click="calculateResult" class="button operator">=</div>
        </div>
      </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CalculadoraComponent",
  props: {
    msg: String,
  },
  data() {
    return {
      output: "",
    };
  },
  methods: {
    clearField() {
      this.output = "0";
    },
    calculatePercent() {
      this.output /= 100;
    },
    updateOutput(value) {
      if (this.output === "0" && value !== ".") {
        this.output = value.toString();
      } else {
        this.output += value.toString();
      }
    },
    calculateResult() {
      this.output = eval(this.output);
    },
  },
};
</script>

<style scoped>

h1 {
  margin: 20px 0;
  text-align: center;
}

.container{
  max-height: 640px;
  max-width: 640px;
}
.container-mg{
  background-color: #2a2d37;
  border-radius: 20px;
  height: 100%;
  width: 100%;
  z-index: 2;
  margin-bottom: 100px;
}
.calculator {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.display {
  background-color: #22252d;
  color: white;
  font-size: 3rem;
  padding: 10px;
  width: 100%;
  text-align: right;
  z-index: -1;
}

.buttons {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
}

.button {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 60px;
  height: 60px;
  font-size: 1.5rem;
  color: white;
  background-color: #282b33;
  border-radius: 10px;
  cursor: pointer;
  margin:5px;
  box-shadow: inset 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.button.operator {
  color: #5cdb95;
}
.button.operator.right {
  color: #ff7f7f;
}

.button.clear.right {
  color: #ff7f7f;
}

.button.double {
  width: 130px;
}

.button:active {
  background-color: lightgray;
  color: black;
}
</style>
