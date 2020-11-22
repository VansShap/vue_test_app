<template>
  <div class="doubt_block">
    <p class="doubt_label">ВСЕ ЕЩЕ СОМНЕВАЕТЕСЬ?</p>
    <p class="doubt_text">Мы даем вам возможность абсолютно бесплатно поучаствовать в пробном уроке</p>
    <div class="doubt_select_block">
      <div class="select_block">
        <custom-select :firstVariant="selectedProgramm" :variants="programmList"></custom-select>
      </div>
      <div class="select_block">
        <custom-select :firstVariant="selectedTeacher" :variants="teacherList"></custom-select>
      </div>
      <div class="select_block">
        <custom-select :firstVariant="selectedPlace" :variants="placeList"></custom-select>
      </div>
      <colorful-button :style="doubtButtonStyle" text="Подобрать урок"></colorful-button>
    </div>
  </div>
</template>

<script>
import ColorfulButton from "./../AdditionalComponents/ColorfulButton.vue"
import CustomSelect from "./../AdditionalComponents/CustomSelect.vue"

export default {
    name: 'DoubtComponent',
    components: {
      ColorfulButton, CustomSelect
    },
    data() {
      return {
        doubtButtonStyle: {  
          'padding': '15px 60px 15px 60px',
          'color': 'white',
          'border-color': 'white',
          'border-width': '1px',
          'background-color': 'transparent',
          'font-weight': '500',
          'align-self': 'baseline'
        },
        selectedProgramm: "Выбрать программу",
        selectedTeacher: "Выбрать преподавателя",
        selectedPlace: "Выбрать место",
        programmList: ["Для начинающих", "Подготовка к IELTS", "Индивидуально"],
        teacherList: ["Jack", "Daniel", "Danny", "Alina"],
        placeList: ["City 13", "City 14", "City 15", "City 16"]
      }
    }
}
</script>

<style scoped>
.doubt_block {
  padding: 5% 8% 5% 8%;
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
  margin-top: 3%;
}

.select_block {
  width: 25%;
  display: flex;
  flex-direction: column;
  background-color: transparent;
  position: relative;
}
</style>