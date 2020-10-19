<template>
  <div class = "story_blocks">
    <template v-for = "story in list" v-bind:key = "story">
      <template v-if = "story.isSelected">
        <div class = "selected_story_block">
          <div class = "selected_story_icon">
            <img class = "selected_story_icon_img" :src = "story.img" />
          </div>
          <div class = "selected_story_form">
            <p class = "selected_story_name">{{story.name}}</p>
            <p class = "selected_story_label">{{story.label}}</p>
            <p class = "selected_story_text">{{story.text}}</p>
          </div>
          <div class = "selected_story_arrows">
            <p class = "slider_arrow" v-on:click = "nextSlide">
              <label class = "arrow">&lt;</label>
            </p>
            <p class = "slider_arrow" v-on:click = "nextSlide">
              <label class = "arrow">&gt;</label>
            </p>
          </div>
        </div>
      </template>
      <template v-else>
        <div class = "story_block">
          <div class = "story_block_icon">
            <img class = "story_block_icon_img" :src = "story.img" />
          </div>
          <p class = "story_block_name">{{story.name}}</p>
          <p class = "story_block_label">{{story.label}}</p>
        </div>
      </template>
    </template>
  </div>
</template>

<script>
export default {
    name: "StoriesComponent",
    props: ['list']
}
</script>

<style>
.story_blocks {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin-left: 80px;
  margin-right: 80px;
  margin-bottom: 70px;
}

.selected_story_block {
  position: relative;
  width: 50%;
  box-shadow: 4px 4px 9px 0 rgb(211, 211, 211);
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}

.selected_story_icon {
  position: absolute;
  top: 15%;
  left: -15%;
  border-radius: 50%;
  width: 130px;
  height: 130px;
}

.selected_story_icon_img {
  display: block;
  width: 100%;
  border-radius: 50%;
}

.selected_story_form {
  padding: 5% 10% 5% 17%;
  text-align: left;
}

.selected_story_name {
  margin-bottom: 0px;
  font-weight: 600;
}

.selected_story_label {
  margin-top: 3px;
  font-size: 13px;
  color: rgb(185, 185, 185);
}

.selected_story_arrows {
  position: absolute;
  bottom: -10%;
  left: 40%;
}

.story_block {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.story_block_name {
  margin-bottom: 0px;
  font-weight: 600;
}

.story_block_label {
  margin-top: 5px;
  font-size: 13px;
  color: rgb(185, 185, 185);
}

.story_block_icon {
  border-radius: 50%;
  width: 75px;
  height: 75px;
}

.story_block_icon_img {
  display: block;
  width:100%;
  border-radius: 50%;
}
</style>