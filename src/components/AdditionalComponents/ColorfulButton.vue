<template>
  <button v-bind:style="style" class="colorful_button">{{text}}</button>
</template>

<script>
export default {
    name: 'ColorfulButton',
    props: { 
      text: {
        type: String,
        required: true
      }, 
      style: {
        type: Object,
        required: true
      }
    }
}
</script>

<style>
.colorful_button {
  display: block;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  height: 50px;
  border-radius: 9px/9px;
  font-size: 16px;
  cursor: pointer;
}

.colorful_button:focus {
  outline: none;
}
</style>