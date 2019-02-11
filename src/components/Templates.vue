<template>
  <div class="templates">
    <div
      class="number-grid"
      :key="value + key"
      v-for="(value, key) in templates"
    >
      <span
        :key="n"
        :class="['spot', { light: i == 0 }]"
        v-for="(i, n) in value"
      ></span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Templates",
  props: ["fields", "patterns"],
  computed: {
    secretTemplates: function() {
      return this.fields.some(f => {
        return f.values[9] === 1;
      })
        ? this.patterns.length
        : 10;
    },
    templates: function() {
      return Object.keys(this.patterns)
        .slice(0, this.secretTemplates)
        .map(i => i.split(""));
    }
  }
};
</script>

<style scoped>
.templates {
  display: grid;
  grid-template-columns: repeat(10, auto);
  grid-gap: 1px;
}

.number-grid {
  display: grid;
  grid-template-columns: repeat(4, 4px);
  grid-template-rows: repeat(7, 4px);
  grid-gap: 1px;
  margin: 0;
  padding: 2px;
  border: 1px solid #333;
  border-radius: 2px;
}

.spot {
  background-color: #333;
}

.light {
  background-color: #fff;
}
</style>
