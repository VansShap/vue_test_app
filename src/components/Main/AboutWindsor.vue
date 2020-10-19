<template>
  <div v-bind:style = "{'background-color': color}" class = "windsor_block">
    <p class = "windsor_block_label">{{label}}</p>
    <p class = "windsor_block_text">{{text}}</p>
  </div>
</template>

<script>
export default {
    name: 'AboutWindsor',
    props: ['color', 'label', 'text']
}
</script>

<style>
.windsor_block {
  width: 45%;
  color: white;
  border-radius: 20px/20px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  text-align: left;
}

.windsor_block_label {
  padding: 30px 30px 0px 70px;
  font-weight: 600;
  font-size: 18px;
  letter-spacing: 2px;
  word-spacing: 1px;
}

.windsor_block_text {
  padding: 5px 120px 30px 70px;
  font-size: 17px;
  line-height: 160%;
}

.windsor_block:first-child {
  margin-left: 80px;
  margin-right: 20px;
}

.windsor_block:last-child {
  margin-left: 20px;
  margin-right: 80px;
}


</style>