<template>
  <header>
    <div class = "slider js-slider">
      <div class = "slider_dot_box">
        <p v-for = "n in sliderList.length" v-bind:class = "{slider_dot_selected: n === sliderActive}" v-bind:key = "n" class = "slider_dot"></p>
        <p class = "slider_arrow" v-on:click = "nextSlide">
          <label class = "arrow">&gt;</label>
        </p>
      </div>
      <div class = "slider_body" v-bind:style = '{left: sliderOffsetLeft + "px"}'>
        <template v-for = 'slide in sliderList' v-bind:key = "slide">
          <header-content :label = "slide.label" :button = "slide.button" :img = "slide.img" :text = "slide.text"></header-content>
        </template>
      </div>
    </div>
  </header>
</template>

<script>
import HeaderContent from "./HeaderContent.vue"

import notebook from "../../assets/notebook.jpg"
import journal from "../../assets/journal.jpg"
import pencil from "../../assets/pencil.jpg"

export default {
    name: 'Header',
    components: {
      HeaderContent
    },
    data() {
      return {
        sliderAllCount: 0, // Всего слайдов
        sliderActive: 1, // Номер активного слайда
        sliderOffsetLeft: 0, // Отступ тела со слайдами в контейнере
        sliderOffsetStep: 0, // Шаг одного слайда = его длина
        sliderList: [
          {label: "Английский с нуля с носителями языка в Москве", text: "Мы приобрели репутацию одного из сильнейших лингвистических центров Москвы. Тысячи людей, пройдя наши курсы, способны свободно общаться на английском языке.", button: "Пройти пробный урок", img: notebook},
          {label: "Lorem ipsum dolor sit amet, consectetur adipiscing elit", text: "Мы приобрели репутацию одного из сильнейших лингвистических центров Москвы. Тысячи людей, пройдя наши курсы, способны свободно общаться на английском языке.", button: "Пройти пробный урок", img: journal},
          {label: "Lorem ipsum dolor sit amet, consectetur adipiscing elit", text: "Мы приобрели репутацию одного из сильнейших лингвистических центров Москвы. Тысячи людей, пройдя наши курсы, способны свободно общаться на английском языке.", button: "Пройти пробный урок", img: pencil}    
        ]
      }
    },
    methods: {
      initSlider: function () {
        // Получаем элементы сладера и его слайдов
        let sliderBody = this.$el.querySelector('.js-slider')
        let sliderSlidies = sliderBody.querySelectorAll('.js-slide')
        // Записываем длину одного слайда для перелистывания
        this.sliderOffsetStep = sliderBody.clientWidth
        // Общее количество слайдов для стопов
        this.sliderAllCount = sliderSlidies.length
      },

      openSlide: function (id) { // Открыть слайд по номеру
        if (id > 0 && id <= this.sliderAllCount) {
          this.sliderActive = id
          // Сдвигаем элемент со слайдами
          this.sliderOffsetLeft = -(this.sliderActive * this.sliderOffsetStep - this.sliderOffsetStep)
        }
      },

      nextSlide: function () { // Следующий слайд
        if (this.sliderActive < this.sliderAllCount) {
          this.sliderActive += 1
          this.openSlide(this.sliderActive)
        }
        else {
          this.sliderActive = 1
          this.openSlide(this.sliderActive)
        }
      },

      prevSlide: function () { // Предыдущий слайд
        if (this.sliderActive > 1) {
          this.sliderActive -= 1
          this.openSlide(this.sliderActive)
        }
      }
    },

    mounted () {
      this.initSlider()
      // Перенастройка слайдера при ресайзе окна
      window.addEventListener('resize', () => {
        this.initSlider()
        this.openSlide(this.sliderActive)
      })
    }
}
</script>

<style>

.slider {
	width: 100%;
	height: 500px;
	position: relative;
	overflow: hidden;
}

.slider_body {
		min-width: auto;
		height: 500px;
		display: flex;
		position: relative;
		align-items: stretch;
		transition: all .5s ease;
}
	
.slider_slide {
		min-width: 100%;
		height: 500px;
		background-size: cover;
		background-position: center;
		flex: 1 100%;
	}

.slider_dot_box {
  position: absolute;
  bottom: 10px;
  left: 10%;
  z-index: 10;
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
}

.slider_arrow:hover {
  box-shadow: -3px 3px 10px 1px rgba(224, 78, 107, 0.7);
}

.slider_dot {
  border-radius: 10px/10px;
  background-color: rgb(184, 184, 184);
  width: 6px;
  height: 6px;
  margin-left: 10px;
  margin-right: 10px;
  margin-top: -1px;
  margin-bottom: 2px;
  display: inline-block;
}  

.slider_dot_selected {
  box-shadow: 0px 0px 6px 2px rgba(224, 78, 107, 0.7);
  background-color: crimson;
  width: 7px;
  height: 7px;
}

.arrow {
  margin-top: 6px;
  display: inline-block;
  color: rgb(156, 156, 156);
  cursor: pointer;
}
</style>