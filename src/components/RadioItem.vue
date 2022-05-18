<script>
import _ from 'lodash';

export default {
  name: "RadioItem",
  props: {
    displayValue: String,
    model: {
      type: [Object, String, Number, Boolean],
    }
  },
  inject: ['radioGroup'],
  data() {
    return {
      isActive: false,
    };
  },
  watch: {
    'radioGroup.modelValue'(newVal) {
      const newVal2 = Object.assign({}, newVal);
      const model2 = Object.assign({}, this.model);
      
      console.log("(newVal, this.model): ", newVal2, model2);
      console.log("_.isEqual(newVal2, model2): ", _.isEqual(newVal2, model2));
      this.setActive(_.isEqual(newVal2, model2));
    }
  },
  methods: {
    setActive(isActive) {
      console.log("setActive, data: ", this.model);
      this.isActive = isActive
    },
    onClick() {
      this.radioGroup.onItemSelected(this.model)
      this.setActive(true)
    }
  }
}
</script>

<template>
  <div @click="onClick()">
    <div :class="['block px-3 py-2 rounded-md', isActive ? 'bg-sky-500 text-white' : 'bg-slate-50']">
      {{ displayValue }}
    </div>
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
