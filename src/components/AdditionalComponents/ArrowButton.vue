<template>
  <div class="slider_arrow" v-bind:class="{slider_arrow_left: direction === 'left', slider_arrow_right: direction === 'right'}" @click="func" v-bind:style="style.button">
    <p class="select_arrow" v-bind:style="style.arrow" ></p>
  </div>
</template>

<script>
export default {
    name: 'ArrowButton',
    props: { 
      func: {
        type: Function,
        default: function() {
          console.log("Default click listener")
        }
      }, 
      style: {
        type: Object,
        required: true
      }, 
      direction: {
        type: String,
        required: true,
        default: "right"
      }
    }
}
</script>

<style>
.select_arrow {
  display: inline-block;
  border: solid rgb(156, 156, 156);
  margin-left: 16px;
  margin-right: 18px;
  border-width: 0 1px 1px 0;
  padding: 3px;
  cursor: pointer;
}

.select_arrow:hover {
  border: solid  rgb(218, 216, 216);
  border-width: 0 1px 1px 0;
}

.slider_arrow {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 30px;
  height: 30px;
  background-color: rgb(255, 251, 251);
  border-radius: 50%;
  cursor: pointer;
  box-shadow: -3px 3px 10px 1px rgba(224, 78, 107, 0.7);
}
</style>