<template>
  <ul class="number-sequence" aria-label="Sequence of checkgrids.">
    <li tabindex="0" :key="i" v-for="(field, i) in fields">
      <ul class="number-grid" :aria-label="`Checkgrid ${i + 1}.`">
        <li v-for="(input, n) of field.inputs" :key="n">
          <label>
            <input
              class="visually-hidden"
              type="checkbox"
              :aria-label="`Spot ${n + 1}`"
              @change="number(i, n, $event);"
            />
            <span class="checkbox-label"></span>
          </label>
        </li>
      </ul>
    </li>
  </ul>
</template>

<script>
export default {
  name: "NumberGrid",
  props: ["fields", "patterns"],
  computed: {
    inputsArray: function() {
      return Array(28).fill();
    }
  },
  methods: {
    number: function(i, n, $event) {
      const values = [...this.fields[i].values];
      const checkedValue = $event.target.checked ? 1 : 0;
      values.splice(n, 1, checkedValue);
      this.fields.splice(i, 1, {
        inputs: this.inputsArray,
        values: values,
        number: this.patterns[values.join("")]
      });
    }
  }
};
</script>

<style scoped>
.number-sequence {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  margin: 15px 0;
  padding: 0;
  list-style: none;
}

.number-sequence li:focus {
  outline: none;
}

.number-grid {
  margin: 10px;
  padding: 0;
  list-style: none;
  position: relative;
  display: grid;
  grid-template-columns: repeat(4, 19px);
  grid-template-rows: repeat(7, 19px);
  border: 1px solid #333;
}

.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  border: 0;
  clip: rect(0 0 0 0);
  overflow: hidden;
}

.checkbox-label {
  display: block;
  width: 100%;
  height: 100%;
  border: 1px solid #333333;
  box-sizing: border-box;
}

input:focus + .checkbox-label {
  background-color: #cccccc;
}

input:checked + .checkbox-label {
  background-color: #444444;
}

input:checked:focus + .checkbox-label {
  background-color: #666666;
}
</style>
