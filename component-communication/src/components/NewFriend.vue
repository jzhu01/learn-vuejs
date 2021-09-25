<template>
  <form>
    <h3>Add a Friend</h3>
    <label>New Friend's Name: </label>
    <input type="text" ref="friendName">
    <br>
    <label>New Friend's Phone Number: </label>
    <input type="text" ref="friendPhoneNumber">
    <br>
    <label>New Friend's Email: </label>
    <input type="text" ref="friendEmail">
    <br>
    <button @click.prevent="submitNewFriend">Submit</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      isFavorite: false
    }
  },
  emits: {
    "new-friend-data": function(friendName, friendEmail, friendPhoneNumber) {
      if (friendName && friendEmail && friendPhoneNumber) {
        return true;
      } else {
        alert("Please provide data for the friend name, email, and phone number.");
        return false;
      }
    }
  },
  methods: {
    submitNewFriend() {
      this.$emit("new-friend-data", this.$refs.friendName.value, this.$refs.friendEmail.value, this.$refs.friendPhoneNumber.value);
    }
  }
}
</script>

<style scoped>
form {
  margin: 0;
  box-sizing: border-box;
  text-align: center;
}
</style>