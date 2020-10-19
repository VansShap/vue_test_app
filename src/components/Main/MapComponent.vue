<template>
  <div class = "map_component_block">
      <div class = "map_component_block_address">
        <p class = "map_component_block_address_label">Адрес</p>
        <p>Юридический: 127473, г. Москва, переулок<br/>Щемиловский 1-й, дом 16, стр. 2</p>
        <p>Фактический: 119415, г. Москва, Ленинский<br/>проспект, дом 96, этаж 1, помещение X</p>
        <p class = "map_component_block_address_label">Контакты</p>
        <p>+7(495)221-08-32<br/>info@windsor.ru<br/>ed@windsor.ru</p>
        <p class = "map_component_block_address_label">Режим и график работы</p>
        <p>Пн-Пт 10.00 - 22.00<br/>Сб-Вс 10.00 - 19.00</p>
      </div>
      <div class = "map_component_block_map">
        <!--<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d1878.6329747418065!2d37.50990432567949!3d55.6668566068203!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x46b54d03af45deed%3A0x3f4c1240dc371504!2z0JvQtdC90LjQvdGB0LrQuNC5INC_0YAt0YIuLCA5Niwg0JzQvtGB0LrQstCwLCDQoNC-0YHRgdC40Y8sIDExNzE5OA!5e0!3m2!1sru!2sby!4v1603050796318!5m2!1sru!2sby" width="600" height="450" frameborder="0" style="border:0;" allowfullscreen="" aria-hidden="false" tabindex="0"></iframe>-->
        <a href="https://yandex.by/maps/213/moscow/?utm_medium=mapframe&utm_source=maps" style="color:#eee;font-size:12px;position:absolute;top:0px;">Москва</a><a href="https://yandex.by/maps/213/moscow/house/leninskiy_prospekt_96/Z04YcwZlS0QPQFtvfXp2cXRrYA==/?ll=37.515219%2C55.670884&utm_medium=mapframe&utm_source=maps&z=16.65" style="color:#eee;font-size:12px;position:absolute;top:14px;">Ленинский проспект, 96 — Яндекс.Карты</a><iframe src="https://yandex.by/map-widget/v1/-/CCQ~m4tg2D" width="100%" height="400" frameborder="1" allowfullscreen="true" style="position:relative;box-shadow: 4px 4px 9px 0 rgb(211, 211, 211);"></iframe>
        <i style = "font-size: 14px; margin-top: 15px; display: block;"><span style = "font-style: normal;">🔎</span> г. Москва, Ленинский проспект, дом 96</i>
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
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
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