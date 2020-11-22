<template>
  <div class="footer_sponsors_block">
    <img class="footer_sponsors_block_img" :src="img"/>
  </div>
</template>

<script>
export default {
  name: "FooterSponsors",
  props: { 
    img: {
      type: String,
      required: true
    }
  }
}
</script>

<style>
.footer_sponsors_block {
  height: 60px;
  margin-top: 80px;
  margin-left: 80px;
  margin-right: 80px;
}

.footer_sponsors_block_img {
  display: block;
  width: 100%;
}
</style>