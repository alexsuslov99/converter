<template>
  <div class="body">
    <slot> </slot>
  </div>
</template>

<script>
export default {
  name: "BodyTest",
};
</script>

<style lang="sass">
.body
  padding: 10px 50px
  display: flex
  justify-content: space-around
</style>
