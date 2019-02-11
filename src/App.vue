<template>
  <div id="app">
    <h2 class="title">Our form is very sophisticated.</h2>
    <b class="subtitle">Please draw your phone number, thanks.</b>
    <NumberGrid :fields="fields" :patterns="patterns" />
    <Templates :fields="fields" :patterns="patterns" />
    <p>Your phone number is</p>
    <PhoneNumber :fields="fields" /> <IsFullNumber v-if="isFullNumber" />
  </div>
</template>

<script>
import NumberGrid from "./components/NumberGrid";
import Templates from "./components/Templates";
import PhoneNumber from "./components/PhoneNumber";
import IsFullNumber from "./components/IsFullNumber";

export default {
  name: "App",
  components: {
    NumberGrid,
    Templates,
    PhoneNumber,
    IsFullNumber
  },
  data() {
    return {
      patterns: {
        "0110100110011001100110010110": 0,
        "0010011000100010001000100010": 1,
        "0110100110010010010010001111": 2,
        "0110100100010010000110010110": 3,
        "1000101010101111001000100010": 4,
        "1111100010001110000110010110": 5,
        "0110100110001110100110010110": 6,
        "1111100100010010001001000100": 7,
        "0110100110010110100110010110": 8,
        "0110100110010111000110010110": 9,
        "1111111111111111111111111111": "💯",
        "1010010110100101101001011010": "🚕",
        "0101101001011010010110100101": "♜",
        "0110111111110110011011111111": "🏎️",
        "0110011011111001111101100110": "⌚",
        "0110111110011001100110011111": "🔋",
        "1111100100110110010000000100": "🤔",
        "0000000000011010010000000000": "✔️",
        "0000000001000000000000000000": "X"
      },
      fields: Array(10).fill({
        inputs: Array(28).fill(),
        values: Array(28).fill(0),
        number: ""
      })
    };
  },
  computed: {
    isFullNumber: function() {
      return this.fields.every(f => f.number || f.number === 0);
    }
  }
};
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.title {
  margin: 0.5em 0;
  font-size: 2.2em;
}

.subtitle {
  margin: 0.5em 0;
  font-size: 1.65em;
}
</style>
