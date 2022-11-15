<script setup>
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import InputField from "./components/InputField.vue";
import SummaryField from "./components/SummaryField.vue";

</script>

<template>
  <div class="header">
    <h3>Budget Calculator</h3>
   
  </div>
  <InputField />
 <SummaryField />
</template>

<style scoped>
.header{
  text-align: center;
}
</style>
