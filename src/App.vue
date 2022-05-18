<script>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import RadioGroup from "./components/RadioGroup.vue";
import RadioItem from "./components/RadioItem.vue";
export default {
  name: "App",
  components: {
    RadioGroup,
    RadioItem,
  },
  data() {
    return {
      items: [
        { displayValue: "1", model: { id: 1 } },
        { displayValue: "-1", model: { id: 2 } },
        { displayValue: "-11", model: { id: 3 } },
        // { displayValue: "-12", model: { id: 4 } },
        // { displayValue: "-14", model: { id: 5 } },
      ],
      selectedModel: null,
    };
  },
};
</script>

<template>
  <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
  <RadioGroup class="flex items-center w-56 mx-auto" v-model="selectedModel">
    <template #default>
      <RadioItem class="chat-notification"
        v-for="(item, index) in items"
        :key="index"
        :displayValue="item.displayValue"
        :model="item.model"
      />
    </template>
  </RadioGroup>
  <div>{{ selectedModel }}</div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.chat-notification {
    display: flex;
    max-width: 24rem;
    margin: 0 auto;
    padding: 1.5rem;
    border-radius: 0.5rem;
    background-color: #fff;
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
  }
</style>
