<template>
  <div class="currency-tabs">
    <div class="currency-tab"
      v-for="(item, index) in items"
      :class="{ active: item.active }"
      :key="index"
      @click="test(index)"
    >
      {{ item.value }}
    </div>
  </div>
</template>

<script>
export default {
  name: "currencyTabs",
  props: {
    items: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    test(index) {
      this.$emit("clickTab", index);
    },
  },
};
</script>

<style lang="sass">
.currency-tabs
  display: flex
  .active
    background-color: #16b67f
    color: white !important
  .currency-tab
    border: 1px solid #cdcdcd
    padding: 10px 25px
    color: black
    &:not(:last-child)
      border-right: 0
</style>