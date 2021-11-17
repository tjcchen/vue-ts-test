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
    <div style="margin-top:10px;">
      <span style="margin-right:10px;">{{ firstName }}</span>
      <span style="margin-right:10px;">{{ lastName }}</span>
      <span style="margin-right:10px;">{{ fullName }}</span>
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

  // Computed properties
  firstName = 'Andy';
  lastName = 'Chen';

  // Declared as computed property getter
  get fullName(): string {
    return this.firstName + ' ' + this.lastName;
  }

  // Declared as computed property setter
  set fullName(value: string) {
    const splited = value.split(' ');
    this.firstName = splited[0];
    this.lastName = splited[1] || '';
  }

  // Methods will be component methods
  increment(): number {
    return this.count++;
  }

  decrement(): number {
    return this.count--;
  }

  // Lifecycle hook
  mounted(): void {
    console.log('this message from lifecycle hook');
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
