<template>
  <div class = "slider_slide js-slide" v-bind:style = '"background-image: url(" + img + ")"'>
    <div class = "content_box">
      <h3 class = "content_label">{{label.toUpperCase()}}</h3>
      <p class = "content_text">{{text}}</p>
      <button class = "content_button">{{button}}</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'HeaderContent',
    props: ['label', 'text', 'img', 'button']
}
</script>

<style>

.content_box {
  margin-left: 50px;
  margin-top: 50px;
}

.content_label {
  width: 33%;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
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
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}

.content_button {
  height: 50px;
  border-radius: 9px/9px;
  padding: 15px 30px 15px 30px;
  color: white;
  background-color: rgb(235, 38, 78);
  box-shadow: 0px 4px 6px 0px rgba(224, 78, 107, 0.7);
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  border-style: none;
  font-size: 16px;
  display: block;
  margin-left: 30px;
  cursor: pointer;
}

.content_button:focus {
    outline: none;
}
</style>