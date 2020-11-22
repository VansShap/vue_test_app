<template>
    <div class="variant">
      <p class="variant_label">{{label}}</p>
      <p class="variant_sublabel">{{sublabel}}</p>
      <p class="variant_text">{{text}}</p>
      <p class="variant_oldprice" v-if="oldprice"><del>{{oldprice}}</del></p>
      <p class="variant_price">{{price}}</p>
      <colorful-button :style="educationVariantButtonStyle" text="Подать заявку"></colorful-button>
    </div>
</template>

<script>
import ColorfulButton from "./../AdditionalComponents/ColorfulButton.vue"

export default {
    name: 'EducationVariant',
    components: {
      ColorfulButton
    },
    data() {
      return {
        educationVariantButtonStyle: {
          'padding': '15px 30px 15px 30px',
          'color': 'white',
          'background-color': 'rgb(235, 38, 78)',
          'box-shadow': '0px 4px 6px 0px rgba(224, 78, 107, 0.7)',
          'border-style': 'none',
          'position': 'absolute',
          'top': '95%',
          'z-index': '10', 
          'align-self': 'center'
        }
      }
    },
    props: { 
      label: {
        type: String,
        requierd: true
      }, 
      sublabel: {
        type: String,
        requierd: true
      }, 
      text: {
        type: String,
        requierd: true
      }, 
      oldprice: {
        type: String
      }, 
      price: {
        type: String,
        requierd: true
      } 
    }
}
</script>

<style>
.variant {
  width: 27%;
  box-shadow: 0px 0px 8px 1px rgb(221, 221, 221);
  border-radius: 10px/10px;
  position: relative;
  display: flex;
  flex-direction: column;
}

.variant:first-child {
  margin-left: 80px;
}

.variant:last-child {
  margin-right: 80px;
}

.variant_label {
  font-weight: 600;
  font-size: 18px;
  letter-spacing: 2px;
  word-spacing: 1px;
  margin-top: 40px;
}

.variant_sublabel {
  text-align: center;
  padding-top: 3%;
  padding-bottom: 3%;
  margin-left: 10%;
  margin-right: 10%;
  font-weight: 400;
  font-size: 16px;
  line-height: 150%;
  border-top-width: 2px;
  border-top-color: silver;
  border-top-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: silver;
  border-bottom-style: solid;
}

.variant_text {
  text-align: center;
  margin-left: 10%;
  margin-right: 10%;
  font-size: 15px;
  line-height: 150%;
  padding-top: 6%;
  padding-bottom: 6%;
}

.variant_oldprice {
  font-size: 16px;
  color:rgb(90, 90, 90);
}

.variant_price {
  font-weight: 400;
  font-size: 22px;
  padding-bottom: 3%;
}
</style>