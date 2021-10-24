<template>
  <child-component
    @emit-fun1="funParent1"
    @emit-fun2="funParent2($event)"
    @emit-fun3="funParent3"
  ></child-component>
  <div>
    <span>{{ dText }}</span>
  </div>
</template>

<script>
import { ref } from "vue";
import childComponentVue from "./components/childComponent.vue";
export default {
  name: "App",
  components: {
    childComponent: childComponentVue,
  },
  setup() {
    const dText = ref("texto original");
    // !!!!!!!!!!!!!!!!!!! begin
    const funParent1 = () => {
      dText.value = "text-changed-by-funParent1";
    };
    const funParent2 = (parameter) => {
      dText.value = "text-changed-by-funParent2    " + parameter;
    };
    const funParent3 = () => {
      dText.value = "text-changed-by-funParent3";
    };
    // !!!!!!!!!!!!!!!!!!! end
    return {
      dText,
      funParent1,
      funParent2,
      funParent3,
    };
  },
};
</script>

<style>
#app {
  height: 400px;
  width: 300px;
  background: green;
}
</style>
