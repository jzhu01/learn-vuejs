<template>
  <form @submit.prevent="submitNewFriend">
    <h3>Add a Friend</h3>
    <div>
      <label>New Friend's Name: </label>
      <input type="text" v-model="friendName">
    </div>
    <div>
      <label>New Friend's Phone Number: </label>
      <input type="text" v-model="friendPhoneNumber">
    </div>
    <div>
      <label>New Friend's Email: </label>
      <input type="text" v-model="friendEmail">
    </div>
    <div>
      <button>Add Contact</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      friendName: "",
      friendPhoneNumber: "",
      friendEmail: "",
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
      this.$emit("new-friend-data", this.friendName, this.friendEmail, this.friendPhoneNumber);
    }
  }
}
</script>

<style scoped>
</style>