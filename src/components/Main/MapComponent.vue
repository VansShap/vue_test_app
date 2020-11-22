<template>
  <div class="map_component_block">
      <div class="map_component_block_address">
        <p class="map_component_block_address_label">Адрес</p>
        <p>Юридический: 127473, г. Москва, переулок<br/>Щемиловский 1-й, дом 16, стр. 2</p>
        <p>Фактический: 119415, г. Москва, Ленинский<br/>проспект, дом 96, этаж 1, помещение X</p>
        <p class="map_component_block_address_label">Контакты</p>
        <p>+7(495)221-08-32<br/>info@windsor.ru<br/>ed@windsor.ru</p>
        <p class="map_component_block_address_label">Режим и график работы</p>
        <p>Пн-Пт 10.00 - 22.00<br/>Сб-Вс 10.00 - 19.00</p>
      </div>
      <div class="map_component_block_map">
        <iframe src="https://yandex.by/map-widget/v1/-/CCQ~m4tg2D" width="100%" height="400" frameborder="1" allowfullscreen="true" style="position:relative;box-shadow: 4px 4px 9px 0 rgb(211, 211, 211);"></iframe>
        <i style="font-size: 14px; margin-top: 15px; display: block;"><span style="font-style: normal;">🔎</span> г. Москва, Ленинский проспект, дом 96</i>
      </div>
  </div>
</template>

<script>
export default {
  name: "MapComponent"
}
</script>

<style>
.map_component_block {
  margin-left: 80px;
  margin-right: 80px;
  display: grid;
  grid-template-rows: 100%;
  grid-template-columns: 30% 70%;
}

.map_component_block_address {
  text-align: left;
}

.map_component_block_address_label {
  margin-top: 30px;
  margin-bottom: 20px;
  font-weight: 600;
  font-size: 17px;
}

.map_component_block_map {
    text-align: right;
}
</style>