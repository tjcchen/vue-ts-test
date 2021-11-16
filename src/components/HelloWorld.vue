<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{ name }}</h2>
    <h3>{{ text }}</h3>
    <div>
      <button v-on:click="decrement">-</button>
      {{ count }}
      <button v-on:click="increment">+</button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  @Prop() private text!: string;

  // Class properties will be component data
  name = "Andy";

  // Class properties will be component data
  count = 0;

  // Methods will be component methods
  increment(): number {
    return this.count++;
  }

  decrement(): number {
    return this.count--;
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
