<template>
  <li>
    <div class="picture_block">
      <img v-bind:src="img"/>
    </div>
    <div class="text_block">
      <p class="for_what_list_label">
        {{title.toUpperCase()}}
      </p>
      <p class="for_what_list_text">{{text}}</p>
    </div>
  </li>
</template>

<script>
export default {
    name: 'ForWhatComponent',
    props: {
      img: {
        type: String,
        requierd: true
      },
      title: {
        type: String,
        requierd: true
      },
      text: {
        type: String,
        requierd: true
      }
    }
}
</script>

<style>
ul.for_what_list li {
  display: flex;
  flex-direction: row;
  width: 33%;
  height: 100%;
}

.picture_block {
  position: relative;
  padding: 4px;
  float: left;
}

.text_block {
  position: relative;
  height: 100%;
  width: 100%;
}

.for_what_list_label {
  color: rgb(0, 0, 0);
  font-weight: 300;
  font-size: 18px;
  text-align: left;
  letter-spacing: 1px;
  word-spacing: 1px;
  width: 60%;
}

.for_what_list_text {
  color: rgb(66, 66, 66);
  font-weight: 200;
  font-size: 14px;
  text-align: left;
  width: 70%;
}
</style>