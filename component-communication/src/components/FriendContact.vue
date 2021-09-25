<template>
  <li>
    <h2>{{ name }} {{isFavorite ? '(Favorite)': ''}} </h2>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="removeFriend">Remove Friend</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  // props: [
  //   'name',
  //   'phoneNumber',
  //   'emailAddress',
  //   'isFavorite'
  // ],
  props: {
    id: String,
    name: String,
    phoneNumber: String,
    emailAddress: String,
    isFavorite: {
      type: Boolean,
      required: false,
      default: false
    }
  },
  emits: ['toggle-favorite', 'remove-friend'],
  data() {
    return {
      detailsAreVisible: false
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit("toggle-favorite", this.id);
    },
    removeFriend(){
      let confirmRemoval = confirm("Are you sure you want to remove friend?");
      if (confirmRemoval) {
        this.$emit("remove-friend", {id: this.id, name: this.name, phone: this.phoneNumber, email: this.emailAddress, isFavorite: this.isFavorite});
      }
    }
  }
};
</script>