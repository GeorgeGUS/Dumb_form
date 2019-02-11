<template>
  <p class="phone-number">
    <span class="prefix">+7</span>
    <span :key="i" v-for="(field, i) in fields">
      <span v-if="i === 0">(</span>
      <span :class="['number', { 'number--in': !!field.number }]">{{
        field.number
      }}</span>
      <span v-if="i === 2">)</span> <span v-if="i === 5 || i === 7">-</span>
    </span>
  </p>
</template>
<script>
export default {
  name: "PhoneNumber",
  props: ["fields"]
};
</script>

<style scoped>
.phone-number {
  margin: 10px;
  font-size: 3em;
  line-height: 1;
}

.prefix {
  letter-spacing: normal;
}

.number {
  display: inline-block;
  vertical-align: bottom;
  margin: 0 3px;
  min-width: 0.7em;
  height: 1em;
  text-align: center;
  border-bottom: 3px solid;
}

.number--in {
  border-bottom: 0;
}
</style>
