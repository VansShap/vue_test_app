<template>
  <div class = "advantages_block">
    <div class = "advantage">
      <p class = "advantage_label">ПРЕПОДАВАТЕЛИ ВЫСШЕЙ КВАЛИФИКАЦИИ</p>
      <p class = "advantage_text">Уровни Beginner и Elementary ведут русскоязычные преподаватели с высшим педагогическим образованием и большим опытом работы</p>
    </div>
    <div class = "advantage">
      <p class = "advantage_label">ПОГРУЖЕНИЕ В ЯЗЫКОВУЮ СРЕДУ</p>
      <p class = "advantage_text">Начиная использовать различные медиа-носители для воссоздания необходимой среды, вы сможете вдвое увеличить эффекимвность от занятий</p>
    </div>
    <div class = "advantage">
      <p class = "advantage_label">ОПТИМАЛЬНАЯ ИНТЕНСИВНОСТЬ</p>
      <p class = "advantage_text">Вы можете овладеть основами языка, научиться применять знания на практике, понимать речь носителей, приобрести правильное произношение</p>
    </div>
  </div>
</template>

<script>
export default {
    name: 'WindsorAdvantages'
}
</script>

<style>
.advantages_block {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin-left: 80px;
  margin-right: 80px;
  margin-bottom: 60px;
}

.advantage {
  width: 30%;
  text-align: left;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}

.advantage_label {
  width: 55%;
  margin-bottom: 15px;
  font-weight: 600;
  font-size: 18px;
  line-height: 150%;
}

.advantage_text {
  width: 85%;
  font-size: 16px;
  line-height: 150%;
}
</style>