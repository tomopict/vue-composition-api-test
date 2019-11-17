<template>
  <div>
    <div class="wrap">
      <h2>Ref</h2>
      <p>{{ RefHelloCount }}</p>
      <button @click="incrementHello">Increment Ref Data</button>
      <h3>animals</h3>
      <ul v-for="(name, index) in Animals" :key="index">
        <li>{{name}}</li>
      </ul>
    </div>
    <div class="wrap">
      <h2>Reactive</h2>
      <p>
        <span>countで表示</span>
        {{count}}
      </p>
    </div>
  </div>
</template>

<script lang="ts">
import { createComponent, reactive, ref, toRefs } from "@vue/composition-api";

export default createComponent({
  setup() {
    /**
     * ref
     */
    const RefHelloCount = ref(1);
    const Animals = ref(["cat", "dog", "hamster"]);

    // NG
    // let RefAnimalObjects = ref({
    //   cat: 1,
    //   dog: 2
    // });

    const incrementHello = () => {
      RefHelloCount.value++;
      // RefAnimalObjects.cat.value++; // NG:Cannot read property 'value' of undefined at incrementHello
    };

    /**
     * reactive
     */

    const ReactiveData = reactive({
      count: 1,
      animals: ["cat", "dog", "hamster"]
    });

    const incrementHelloReactve = () => {
      ReactiveData.count++;
    };

    // 単一の場合は
    // return toRefs(ReactiveData);

    // 複数の場合
    return {
      RefHelloCount,
      Animals,
      ...toRefs(ReactiveData),
      incrementHello
    };
  }
});
</script>
<style lang="scss" scoped>
.wrap {
  border: #000 1px solid;
}
</style>

