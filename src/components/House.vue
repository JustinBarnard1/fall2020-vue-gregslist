<template>
  <div class="col-4 house">
    <router-link :to="{name: 'HouseDetails', params: { id: houseData._id}}">
      <div class="card">
        <img class="card-img-top" :src="houseData.imgUrl" alt />
        <div class="card-body">
          <h4
            class="card-title"
          >Year: {{houseData.year}} Bed: {{houseData.bedrooms}} Bath: {{houseData.bathrooms}}</h4>
          <p>${{houseData.price}}</p>
        </div>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: "House",
  props: {
    houseData: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.house {
  transition: 0.5s ease;
  cursor: pointer;
}
.house:hover {
  transform: scale(1.05);
}
</style>