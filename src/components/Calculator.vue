<template>
  <div class="container">
    <div class="calculator" :class="{ dark: isDark }">
      <div class="theme-toggler" @click="toggleTheme">
        <i class="toggler-icon" :class="{ active: isDark }"></i>
      </div>
      <div class="display-screen">
        <div id="display">{{ displayText }}</div>
      </div>
      <div class="buttons">
        <table>
          <tr>
            <td><button class="btn-operator" @click="clear">C</button></td>
            <td><button class="btn-operator" @click="appendToDisplay('/')">&divide;</button></td>
            <td><button class="btn-operator" @click="appendToDisplay('*')">&times;</button></td>
            <td><button class="btn-operator" @click="backspace">DEL</button></td>
          </tr>
          <tr>
            <td><button class="btn-number" @click="appendToDisplay('7')">7</button></td>
            <td><button class="btn-number" @click="appendToDisplay('8')">8</button></td>
            <td><button class="btn-number" @click="appendToDisplay('9')">9</button></td>
            <td><button class="btn-operator" @click="appendToDisplay('-')">-</button></td>
        </tr>
        <tr>
        <td><button class="btn-number" @click="appendToDisplay('4')">4</button></td>
            <td><button class="btn-number" @click="appendToDisplay('5')">5</button></td>
            <td><button class="btn-number" @click="appendToDisplay('6')">6</button></td>
            <td><button class="btn-operator" @click="appendToDisplay('+')">+</button></td>
        </tr>
        <tr>
          <td><button class="btn-number" @click="appendToDisplay('1')">1</button></td>
          <td><button class="btn-number" @click="appendToDisplay('2')">2</button></td>
          <td><button class="btn-number" @click="appendToDisplay('3')">3</button></td>
          <td rowspan="2"><button class="btn-equal" @click="evaluate">=</button></td>
        </tr>
        <tr>
          <td><button class="btn-operator" @click="appendToDisplay('(')">(</button></td>
          <td><button class="btn-number" @click="appendToDisplay('0')">0</button></td>
          <td><button class="btn-operator" @click="appendToDisplay(')')">)</button></td>
        </tr>

        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      displayText: "",
      isDark: true,
    };
  },
  methods: {
    clear() {
      this.displayText = "";
    },
    backspace() {
      this.displayText = this.displayText.slice(0, -1);
    },
    appendToDisplay(value) {
      this.displayText += value;
    },
    toggleTheme() {
      this.isDark = !this.isDark;
    },
    backspace() {
    this.displayText = this.displayText.slice(0, -1);
    },
    evaluate() {
    try {
      this.displayText = eval(this.displayText);
    } catch (error) {
      this.displayText = "Error";
    }
  },
  },
};
</script>
