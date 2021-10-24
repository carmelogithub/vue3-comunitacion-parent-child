<template>
  <div class="child-container">
    <button @click="fun1()">boton 1</button>
    <button @click="fun2()">boton 2</button>
    <button @click="$emit('emit-fun3')">boton 3</button>
  </div>
</template>

<script>
export default {
  name: "childComponent",
  emits: ["emit-fun1", "emit-fun2", "emit-fun3"],
  setup(props, { emit }) {
    const fun1 = () => {
      emit("emit-fun1");
    };
    const fun2 = () => {
      emit("emit-fun2", "parameter-from-child");
    };
    return {
      fun1,
      fun2,
    };
  },
};
</script>

<style scoped>
.child-container {
  width: 100px;
  height: 200px;
  background: red;
}
</style>