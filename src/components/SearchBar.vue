<template>
  <div>
    <input @input="onInputChange" />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInputChange: function(event) {
      //console.log(event.target.value);
      this.$emit("termChange", event.target.value);
    }
  }
};
</script>

<style scoped>
</style>