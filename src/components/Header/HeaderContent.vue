<template>
  <div class="slider_slide js-slide" v-bind:style='"background-image: url(" + img + ")"'>
    <div class="content_box">
      <h3 class="content_label">{{label.toUpperCase()}}</h3>
      <p class="content_text">{{text}}</p>
      <colorful-button :style="headerContentButtonStyle" :text="button"></colorful-button>
    </div>
  </div>
</template>

<script>
import ColorfulButton from "./../AdditionalComponents/ColorfulButton.vue"

export default {
    name: 'HeaderContent',
    components: {
      ColorfulButton
    },
    data() {
      return {
        headerContentButtonStyle: {
          'padding': '15px 30px 15px 30px',
          'color': 'white',
          'background-color': 'rgb(235, 38, 78)',
          'box-shadow': '0px 4px 6px 0px rgba(224, 78, 107, 0.7)',
          'border-style': 'none',
          'margin-left': '30px'
        }
      }
    },
    props: { 
      label: {
        type: String,
        requred: true
      }, 
      text: {
        type: String,
        required: true
      }, 
      img: {
        type: String,
        required: true
      }, 
      button: {
        type: String,
        required: true
      }
    }
}
</script>

<style>

.content_box {
  margin-left: 50px;
  margin-top: 50px;
}

.content_label {
  width: 33%;
  color: rgb(0, 0, 0);
  font-weight: 900;
  font-size: 28px;
  text-align: left;
  margin-top: 30px;
  margin-bottom: 30px;
  margin-left: 30px;
  letter-spacing: 1px;
  word-spacing: 1px;
}

.content_text {
  width: 33%;
  font-size: 16px;
  text-align: left;
  font-weight: 300;
  margin-left: 30px;
  margin-bottom: 30px;
  color: rgb(66, 66, 66);
}
</style>