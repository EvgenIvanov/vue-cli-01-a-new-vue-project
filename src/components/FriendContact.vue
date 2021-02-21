<template>
  <li>
    <h2>{{ name }} {{ friendIsFavorite ? '(Favorite)' : '' }}</h2>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? 'Hide' : 'Show' }} Detail
    </button>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ phoneNumber }}</li>
      <li><strong>Email:</strong> {{ emailAddress }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  // props: ['name', 'phoneNumber', 'emailAddress', 'isFavorite'],
  props: {
    name: { type: String, requared: true },
    phoneNumber: { type: String, requared: true },
    emailAddress: { type: String, requared: true },
    isFavorite: {
      type: Boolean,
      requared: false,
      default: false
      // validator: function(value) {
      //   return value === '1' || value === '0';
      // }
    }
  },
  data() {
    return {
      detailsAreVisible: false,
      friendIsFavorite: this.isFavorite,
      friend: {
        id: 'manuel',
        name: 'Manuel Lorenz',
        phone: '1379 13971 90',
        email: 'manuel@localhost.com'
      }
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.friendIsFavorite = !this.friendIsFavorite;
      // if (this.friendIsFavorite === '1') {
      //   this.friendIsFavorite = '0';
      // } else {
      //   this.friendIsFavorite = '1';
      // }
    }
  }
};
</script>
