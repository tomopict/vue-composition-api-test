<template>
  <div>
    <button @click="increment">Count is: {{ this.count }}, double is: {{ this.double }}</button>
    <h2>{{ propHello }}</h2>
    <h3>{{ reactiveMessage }}</h3>
    <p>{{ info }}</p>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import axios from "axios";
import { AxiosPromise } from "axios";

@Component
export default class HelloWorld extends Vue {
  // props
  @Prop() private propHello!: string;

  // data
  reactiveMessage: string = "Hello";
  info: any = {};
  count: number = 0;

  // computed
  get double() {
    return this.count * 2;
  }

  // mounted
  mounted() {
    this.getDate();
  }

  // methods
  getDate() {
    axios
      .get("https://api.coindesk.com/v1/bpi/currentprice.json")
      .then(response => (this.info = response));
  }
  increment() {
    this.count++;
  }
}
</script>
