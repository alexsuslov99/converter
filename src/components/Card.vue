<template>
  <div class="test-card">
    <div class="card-title">{{ title }}</div>
    <currency-tabs :items="tabsItems" @clickTab="test" />
    <div class="test-input">
      <input class="test-card-price" type="text" value="5 000" />
      <div v-if="currency" class="test-card-currency">
        {{ currency }}
      </div>
    </div>
  </div>
</template>

<script>
import currencyTabs from "./currencyTabs.vue";
export default {
  name: "CardCurrency",
  components: {
    currencyTabs,
  },
  data() {
    return {
      items: [
        { value: "RUR", active: false },
        { value: "EUR", active: false },
        { value: "USD", active: false },
        { value: "GBR", active: false },
      ],
      currency: "",
    };
  },
  props: {
    title: {
      type: String,
      default: "",
    },
  },

  computed: {
    tabsItems() {
      this.items.push({ value: ">", active: false });
      return this.items;
    },
  },
  methods: {
    test(index) {
      this.items.map((item, idx) => {
        if (idx === index) {
          this.items[index] = {
            ...this.items[index],
            active: !this.items[index].active,
          };
          if (index !== this.items.length - 1) {
            this.currency = this.items[index].value;
          }
        } else {
          this.items[idx] = {
            ...this.items[idx],
            active: false,
          };
        }
      });
    },
  },
};
</script>

<style lang="sass">
.test-card
  .currency-tabs
    margin-bottom: 10px
  .test-input
    height: 80px
    border: 2px solid #cdcdcd
    width: 395px
    padding: 5px 10px
    .test-card-currency
      font-weight: 500
      color: #9c9898
    .test-card-price
      height: 50px
      font-size: 25px
      max-width: 280px
      padding: 0
      border: none
      font-weight: 700
      &:focus-visible
        outline: none
  .card-title
    font-size: 16px
    color: #777
    margin: 10px 0 5px
</style>