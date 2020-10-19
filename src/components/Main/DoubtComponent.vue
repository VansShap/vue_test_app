<template>
  <div class = "doubt_block">
    <p class = "doubt_label">ВСЕ ЕЩЕ СОМНЕВАЕТЕСЬ?</p>
    <p class = "doubt_text">Мы даем вам возможность абсолютно бесплатно поучаствовать в пробном уроке</p>
    <div class = "doubt_select_block">
      <div class = "select_block">
        <div class = "select_head">{{selectedProgramm}} <p @click = "isDropped1 = !isDropped1" class="select_arrow" v-bind:class = "{select_arrow_active: isDropped1}"></p></div>
        <div class = "select_item" v-bind:class = "{select_item_active: isDropped1}" v-for = "variant in programmList" v-bind:key = "variant" @click = "selectProgram(variant)">{{variant}}</div>
      </div>
      <div class = "select_block">
        <div class = "select_head">{{selectedTeacher}} <p @click = "isDropped2 = !isDropped2" class="select_arrow" v-bind:class = "{select_arrow_active: isDropped2}"></p></div>
        <div class = "select_item" v-bind:class = "{select_item_active: isDropped2}" v-for = "variant in teacherList" v-bind:key = "variant" @click = "selectTeacher(variant)">{{variant}}</div>
      </div>
      <div class = "select_block">
        <div class = "select_head">{{selectedPlace}} <p @click = "isDropped3 = !isDropped3" class="select_arrow" v-bind:class = "{select_arrow_active: isDropped3}"></p></div>
        <div class = "select_item" v-bind:class = "{select_item_active: isDropped3}" v-for = "variant in placeList" v-bind:key = "variant" @click = "selectPlace(variant)">{{variant}}</div>
      </div>
      <button class = "select_button">Подобрать урок</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'DoubtComponent',
    data() {
      return {
        isDropped1: false,
        isDropped2: false,
        isDropped3: false,
        selectedProgramm: "Выбрать программу",
        selectedTeacher: "Выбрать преподавателя",
        selectedPlace: "Выбрать место",
        programmList: ["Для начинающих", "Подготовка к IELTS", "Индивидуально"],
        teacherList: ["Jack", "Daniel", "Danny", "Alina"],
        placeList: ["City 13", "City 14", "City 15", "City 16"]
      }
    },
    methods: {
      selectProgram: function(variant) {
        this.selectedProgramm = variant;
        this.isDropped1 = false;
      },

      selectTeacher: function(variant) {
        this.selectedTeacher = variant;
        this.isDropped2 = false;
      },

      selectPlace: function(variant) {
        this.selectedPlace = variant;
        this.isDropped3 = false;
      }
    }
}
</script>

<style>
.doubt_block {
  padding: 5% 8% 5% 8%;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  background-color: rgb(255, 81, 81);
  color: white;
  text-align: left;
  margin-bottom: 60px;
}

.doubt_label {
  font-weight: 600;
  font-size: 24px;
  letter-spacing: 1px;
}

.doubt_text {
  width: 40%;
  font-weight: 500;
  font-size: 18px;
}

.doubt_select_block {
  display: flex;
  justify-content: space-between;
  flex-direction: row;
}

.select_block {
  width: 25%;
  display: flex;
  flex-direction: column;
  background-color: transparent;
}

.select_head {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  font-size: 15px;
  padding-bottom: 4px;
  color: rgb(185, 185, 185);
  border-bottom-color: rgb(185, 185, 185);
  border-bottom-width: 1px;
  border-bottom-style: solid;
}

.select_item {
  display: none;
}

.select_item_active {
  display: block;
  font-size: 15px;
  padding-top: 8px;
  padding-bottom: 8px;
  background-color:  rgb(202, 202, 202);
  border-bottom-color: rgb(168, 168, 168);
  border-bottom-width: 1px;
  border-bottom-style: solid;
  text-align: center;
}

.select_item_active:hover {
  background-color:  rgba(202, 202, 202, 0.5);
  color: rgba(0, 0, 0, 0.5);
  cursor: pointer;
}

.select_arrow {
  display: inline-block;
  border: solid rgb(168, 168, 168);
  border-width: 0 1px 1px 0;
  display: inline-block;
  padding: 3px;
  transform: rotate(45deg);
  cursor: pointer;
}

.select_arrow:hover, .select_arrow_active:hover{
  border: solid  rgb(185, 185, 185);
  border-width: 0 1px 1px 0;
}

.select_arrow_active {
  transform: rotate(-135deg);
}

.select_button {
  height: 50px;
  border-radius: 9px/9px;
  padding: 15px 60px 15px 60px;
  color: white;
  border-color: white;
  border-width: 1px;
  background-color: transparent;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-size: 16px;
  font-weight: 500;
  display: block;
  cursor: pointer;
  align-self: baseline;
}

.select_button:focus {
  outline: none;
}
</style>