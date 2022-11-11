<template>
  <div>
    <div class="espaco">
      <slot></slot>
    </div>
  </div>
</template>

<style scoped>
.espaco {
  border: 1px solid black;
  text-align: center;
  padding: 20px;
  border: 3px solid black;
  height: 100%;
}
</style>

<script>
export default {
  name: "TotaisComponent",
  data() {
    return {};
  },
  methods: {},
};
</script>
