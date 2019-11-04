<template>
  <div>
    <HelloCompostion propHello="HelloComposition" />
    <hr />
    <HelloWorld propHello="HelloWorld" />
  </div>
</template>

<script>
import HelloCompostion from "@/components/HelloCompostion.vue";
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  components: {
    HelloCompostion,
    HelloWorld
  }
};
</script>