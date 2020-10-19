<template>
  <div class = "actual_label">
    <h4 class = "actual_header">ВСЕ САМОЕ АКТУАЛЬНОЕ</h4>
    <div>
      <p class = "slider_arrow" v-on:click = "nextSlide">
        <label class = "arrow">&lt;</label>
      </p>
      <p class = "slider_arrow" v-on:click = "nextSlide">
        <label class = "arrow">&gt;</label>
      </p>
    </div>
  </div>
  <div class = "actual_blocks">
    <template v-for = "act in list" v-bind:key = "act">
      <div class = "actual_block">
        <div class = "actual_first_line">
          <img class = "actual_first_line_img" :src = "act.img" />
        </div>
        <p class = "actual_second_line">{{act.text}}</p>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: 'ActualComponent',
  props: ['list']
}
</script>

<style>
.actual_label {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin-left: 80px;
  margin-right: 80px;
}


.actual_header {
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  color: rgb(0, 0, 0);
  font-weight: 600;
  font-size: 24px;
  text-align: left;
  letter-spacing: 1px;
  word-spacing: 1px;
}

.arrow {
  margin-top: 6px;
  display: inline-block;
  color: rgb(156, 156, 156);
  cursor: pointer;
}

.slider_arrow {
  margin-left: 10px;
  margin-right: 10px;
  display: inline-block;
  width: 30px;
  height: 30px;
  background-color: rgb(255, 251, 251);
  border-radius: 20px/20px;
  cursor: pointer;
  box-shadow: -3px 3px 10px 1px rgba(224, 78, 107, 0.7);
}

.arrow:hover {
  color: rgb(211, 211, 211);
}

.actual_blocks {
  display: flex;
  flex-direction: row;
  justify-content: center;
  margin-left: 80px;
  margin-right: 80px;
  margin-bottom: 70px;
}

.actual_block {
  display: grid;
  grid-template-columns: auto;
  grid-template-rows: auto auto;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  margin-left: 20px;
  margin-right: 20px;
}

.actual_first_line {
  border-radius: 9px/9px;
  box-shadow: 4px 4px 9px 0 rgb(211, 211, 211);
  width: auto;
  padding-top: 20px;
  padding-bottom: 40px;
  padding-right: 15%;
  padding-left: 15%;
  height: 260px;
}

.actual_first_line_img {
  display: block;
  border-radius: 9px/9px;
  width:100%;
  height: 100%;
}

.actual_second_line {
  text-align: center;
  margin: auto;
  font-size: 16px;
  width: 65%;
  margin-top: 20px;
}
</style>