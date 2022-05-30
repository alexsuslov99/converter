<template>
<header-test />
<body-test>
  <card-currency title="У меня есть" />
      <div class="card-reverse" :style="cssProps" />
      <card-currency title="Хочу приобрести" />
    </body-test>
</template>

<script>
import HeaderTest from "./components/Header.vue";
import BodyTest from "./components/Body.vue";
import CardCurrency from "./components/Card.vue";
export default {
  name: 'App',
  components: {
    HeaderTest,
    BodyTest,
    CardCurrency,
  },
  data() {
    return {
      cssProps: {
        backgroundImage: `url(${require("@/assets/transfer.svg")})`,
      },
    };
  },
}
</script>

<style>
*,
*::before,
*::after {
  box-sizing: border-box;
}
body {
  margin: 0;
}

.card-reverse {
  width: 95px;
  height: 95px;
  background-repeat: no-repeat;
  align-self: center;
}
</style>
