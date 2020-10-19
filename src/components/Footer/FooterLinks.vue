<template>
  <div class = "footer_links_block">
    <div class = "footer_links_block_logo">
      <img class = "footer_links_block_logo_img" :src = "img" />
    </div>
    <div class = "footer_links_block_links">
      <a class = "footer_links_block_link">О школе</a>
      <a class = "footer_links_block_link">Курсы</a>
      <a class = "footer_links_block_link">Преподаватели</a>
      <a class = "footer_links_block_link">Новости</a>
      <a class = "footer_links_block_link">Расписание</a>
    </div>
    <div>+7 (495) 221 - 08 - 32</div>
  </div>
</template>

<script>
export default {
  name: "FooterLinks",
  props: ['img']
}
</script>

<style>
.footer_links_block {
  margin-top: 80px;
  margin-left: 80px;
  margin-right: 80px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: row;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  height: 20px;
}

.footer_links_block_logo {
  width: 15%;
}

.footer_links_block_logo_img {
  width: 100%;
  height: 100%;
  display: block;
}

.footer_links_block_links {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: row;
}

.footer_links_block_link {
  white-space: nowrap;
  margin-right: 10%;
}

.footer_links_block_link:hover {
  cursor: pointer;
  color: rgb(211, 211, 211);
}

.footer_links_block_link:last-child {
  margin-right: 0;
}
</style>