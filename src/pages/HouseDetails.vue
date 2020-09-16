<template>
  <div id="house-details" class="container">
    <div v-if="house._id" class="col-4">
      <div class="card">
        <img class="card-img-top" :src="house.imgUrl" alt />
        <div class="card-body">
          <h4
            class="card-title"
          >Year: {{house.year}} Bed: {{house.bedrooms}} Bath: {{house.bathrooms}}</h4>
          <p class="card-text">{{house.description}}</p>
          <div class="d-flex justify-content-between">
            <button class="btn btn-outline-danger" @click="removeHome">Delete</button>
            <button class="btn btn-outline-info" @click="bid">+ $1000</button>
            <p>${{house.price.toFixed(2)}}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "House-Details",
  mounted() {
    this.$store.dispatch("getHouseById", this.$route.params.id);
  },
  data() {
    return {};
  },
  computed: {
    house() {
      return this.$store.state.activeHouse;
    },
  },
  methods: {
    removeHome() {
      this.$store.dispatch("deleteHouse", this.house._id);
    },
    bid() {
      let bid = { id: this.house._id, price: this.house.price + 1000 };
      this.$store.dispatch("bid", bid);
    },
  },
};
</script>

<style>
</style>