<template>
  <div v-if="doggy.id <= limit">
    <div class="product container-fluid">
      <div class="img-cut"><img :alt="'>>>>>>>>>'+doggy.name + ' preview'" :src="doggy.image.url" /></div>

      <p class="type">{{ doggy.life_span }}</p>
      <p class="name">{{ doggy.name }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["doggy", "limit"],
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap");
.product {
  margin: 0;
  padding: 0;
  border: 3px solid #f2f2f2;
}
.product .img-cut {
  aspect-ratio: 4 / 3;
  object-fit: contain;
  overflow: hidden;
}
.product img {
  width: 120%;
  position: relative;
  left: -10%;
  object-fit: contain;
}
.product .type {
  margin: 10px 0 8px 28px;
  font-weight: 600;
  font-size: 13px;
  letter-spacing: -0.03em;
  text-transform: uppercase;
  color: #232323;
  line-height: 20px;
}
.product .name {
  margin: 0 0 28px 28px;
  font-weight: 700;
  font-size: 19px;
  color: #232323;
  line-height: 28px;
}
</style>
