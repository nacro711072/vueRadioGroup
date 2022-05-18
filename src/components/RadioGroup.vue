<template>
  <div>
    <slot :selectItem="onItemSelected"></slot>
  </div>

</template>

<style scoped>
a {
  color: #42b983;
}
</style>

<script>
export default {
  name: "RadioGroup",
  props: {
      modelValue: ''
  },
  data() {
    return {
      activeMethods: [
        function () {
          console.log(this)
        }
      ]
    }
  },
  mounted() {
  },
  methods: {
    onItemSelected(model) {
      // const allItems = this.$slots.default()[0].children.filter(node => {
      //   return node.type.name === 'RadioItem';
      // })
      // console.log("onItemSelected");
      this.$emit('update:modelValue', model);
      // console.log("onItemSelected, modelValue: ", this.modelValue);
      // for (let i = 0; i < allItems.length; i++) {
        
      //   const element = this.$slots.default()[0].children[i];
      //   element.type.methods.setActive(false)

      // }
      // allItems.forEach(x => x.type.methods.setActive(false))
      // this.activeMethods.forEach(setActive => {setActive(false)});
    }
  },
  provide() {
    return {
      radioGroup: this,
    }
  }
};
</script>
