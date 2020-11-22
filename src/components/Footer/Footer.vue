<template>
  <footer>
      <footer-sponsors :img="img"></footer-sponsors>
      <footer-links :img="logo"></footer-links>
  </footer>
</template>

<script>
import FooterSponsors from "./FooterSponsors.vue"
import FooterLinks from "./FooterLinks.vue"

import logos from "../../assets/logos.png"
import logo from "../../assets/logo.png"

export default {
    name: 'Footer',
    components: {
      FooterSponsors, FooterLinks
    },
    data() {
      return {
        img: logos,
        logo: logo
      }
    }
}
</script>