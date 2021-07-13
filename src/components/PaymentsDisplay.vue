<template>
  <div class="payments-list">
    <div># - data - category - value</div>
    <div v-for="(item, idx) in list" :key="idx">
      {{ idx + 1 }}) {{ item.date }} - {{ item.category }} - {{ item.value }}
    </div>
  </div>
</template>

<script>
export default {
  name: "PaymentsDisplay",
  props: {
    list: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {};
  },
};
</script>

<style>
</style>