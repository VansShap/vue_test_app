<template>
  <div class = "teachers_label">
    <h4 class = "teachers_header">ПРЕПОДАВАТЕЛИ WINDSOR</h4>
    <div>
      <p class = "slider_arrow" v-on:click = "nextSlide">
        <label class = "arrow">&lt;</label>
      </p>
      <p class = "slider_arrow" v-on:click = "nextSlide">
        <label class = "arrow">&gt;</label>
      </p>
    </div>
  </div>
  <div class = "teacher_blocks">
    <template v-for = "teacher in list" v-bind:key = "teacher">
      <div class = "teacher_block">
        <div class = "teacher_first_line_icon">
          <img class = "teacher_first_line_icon_img" :src = "teacher.img" />
        </div>
        <p class = "teacher_first_line_name">{{teacher.name}}</p>
        <p class = "teacher_first_line_state">{{teacher.state}}</p>
        <p class = "teacher_second_line">{{teacher.text}}</p>
      </div>
    </template>
  </div>
</template>

<script>

export default {
  name: 'TeachersComponent',
  props: ['list']
}
</script>

<style>
.teachers_label {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin-left: 80px;
  margin-right: 80px;
}


.teachers_header {
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

.teacher_blocks {
  display: flex;
  flex-direction: row;
  justify-content: center;
  margin-left: 80px;
  margin-right: 80px;
  margin-bottom: 60px;
}

.teacher_block {
  display: grid;
  grid-template-columns: 33% auto;
  grid-template-rows: auto auto auto;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  margin-left: 20px;
  margin-right: 20px;
}

.teacher_first_line_icon {
  grid-row-start: 1;
  grid-row-end: 3;
  grid-column-start: 1;
  grid-column-end: 2;
  border-radius: 50%;
  width: 75px;
  height: 75px;
}

.teacher_first_line_icon_img {
  display: block;
  width:100%;
  border-radius: 50%;
}

.teacher_first_line_name {
  text-align: left;
  grid-row-start: 1;
  grid-row-end: 2;
  grid-column-start: 2;
  grid-column-end: 3;
  margin-bottom: 0px;
  font-size: 18px;
  font-weight: 600;
}

.teacher_first_line_state {
  grid-row-start: 2;
  grid-row-end: 3;
  grid-column-start: 2;
  grid-column-end: 3;
  margin-top: 4px;
  text-align: left;
  font-size: 16px;
  color: rgb(185, 185, 185);
}

.teacher_second_line {
  grid-row-start: 3;
  grid-row-end: 4;
  grid-column-start: 1;
  grid-column-end: 3;
  text-align: justify;
  line-height: 150%;
}
</style>