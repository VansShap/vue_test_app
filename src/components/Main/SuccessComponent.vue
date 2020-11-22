<template>
  <div class="success_block">
    <div>
      <p class="success_label">ЛЕКСИЧЕСКИЙ ПОДХОД</p>
      <p class="success_text">В его основе - изучение словосочетаний, фраз и выражений в контексте, а также их активное использование. Это можно сравнить с тем, как изучается родной язык.</p>
    </div>
    <div>
      <p class="success_label">ОПТИМАЛЬНЫЙ БАЛАНС</p>
      <p class="success_text">Слушание языка, коммуникация как с самим преподавателем, так и со студентами в группе, само говорение студента - проходят максимально выверено.</p>
    </div>
    <div class="image_column" v-bind:style='"background-image: url(" + img + ")"'></div>
    <div>
      <p class="success_label">ЗАРУБЕЖНЫЕ ПРЕПОДАВАТЕЛИ</p>
      <p class="success_text">Высококлассная команда носителей языка, из Великобритании, США и Канады, которые имеют высшее образование и квалификацию международного уровня.</p>
    </div>
    <div>
      <p class="success_label">ПСИХОЛОГИЧЕСКИЙ ТРЕНИНГ</p>
      <p class="success_text">Позволяет минимизировать стресссовое состояние при переходе на английский язык, способствует разрушению языкового барьера, препятствует его появлению.</p>
    </div>
  </div>
</template>

<script>
export default {
    name: 'SuccessComponent',
    props: {
      img: {
        type: String,
        requierd: true
      } 
    }
}
</script>

<style>
.success_block {
  display: grid;
  grid-template-columns: auto 33% auto;
  grid-template-rows: auto auto;
  margin-left: 80px;
  margin-right: 80px;
  margin-bottom: 60px;
}

.image_column {
  background-repeat: no-repeat;
  background-size: 100% auto;
  grid-column-start:2;
  grid-row-start: 1;
  grid-row-end: 3;
  margin-left: 4%;
  margin-right: 4%;
}

.success_label {
  text-align: left;
  font-weight: 600;
  font-size: 18px;
}

.success_text {
  text-align: left;
  font-size: 16px;
  line-height: 150%;
}
</style>