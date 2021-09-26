<template>
  <h2>Manage Goals</h2>
  <input type="text" ref="goal"/>
  <button @click="setGoal">Set Goal</button>
  <teleport to="body">
    <error-alert v-if="inputIsInvalid">
      <h2>Input is Invalid!</h2>
      <p>Please enter a few characters...</p>
      <button @click="confirmError">Okay</button>
    </error-alert>
  </teleport>
</template>

<script>
import ErrorAlert from "../layout/ErrorAlert";
export default {
  components: {ErrorAlert},
  data(){
    return {
      inputIsInvalid: false
    }
  },
  methods: {
    setGoal() {
      const enteredVal = this.$refs.goal.value;
      if (enteredVal === '') {
        this.inputIsInvalid = true;
      }
    },
    confirmError() {
      this.inputIsInvalid = false;
    }
  }
}
</script>

<style scoped>

</style>