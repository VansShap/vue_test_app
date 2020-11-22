<template>
  <div class="canvas_textblock">
    <div class="textblock">
      <p class="number">01</p>
      <p class="text">Вы оставляете заявку на сайте или звоните нам в офис</p>
    </div>
    <div class="textblock">
      <p class="number">02</p>
      <p class="text">Мы определяем уровень вашего знания языка при помощи теста</p>
    </div>
    <div class="textblock">
      <p class="number">03</p>
      <p class="text">Мы подбираем вам учебный план, и вы приступаете к занятиям</p>
    </div>
    <div class="textblock">
      <p class="number">04</p>
      <p class="text">По окончании курса мы выдаем вам сертификат</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CanvasComponent'
}
</script>

<style>
.canvas_textblock {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
}

.text {
  text-align: left;
  padding-left: 20px;
}

.number {
  position: absolute;
  -webkit-text-fill-color: white;
  -webkit-text-stroke-width: 1px;
  -webkit-text-stroke-color: rgb(219, 219, 219);
  font-size: 80px;
  margin-top: -45px;
  z-index: -10;
}

.textblock {
  width: 22%;
  margin-top: 80px;
  font-size: 17px;
}

#canvas_1 {
  position: absolute;
  left: 30%;
  height: 40px;
  width: 30%;
}

#canvas_2 {
  position: absolute;
  height: 40px;
  width: 30%;
}

#canvas_3 {
  position: absolute;
  height: 40px;
  width: 30%;
}
</style>