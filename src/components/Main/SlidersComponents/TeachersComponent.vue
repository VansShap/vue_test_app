<template>
  <div class="teachers_label">
    <h4 class="teachers_header">ПРЕПОДАВАТЕЛИ WINDSOR</h4>
    <div style="display: flex; flex-direction: row">
      <arrow-button :func="controlClick" direction="left" :style="teachersArrowButtonStyleFirst"></arrow-button>
      <arrow-button :func="controlClick" direction="right" :style="teachersArrowButtonStyleSecond"></arrow-button>
    </div>
  </div>
  <div class="teachers_slider">
    <div class="teacher_blocks">
      <template v-for="teacher in list" v-bind:key="teacher">
        <div class="slider_teacher_block">
          <div class="teacher_block">
            <div class="teacher_first_line_icon">
              <img class="teacher_first_line_icon_img" :src="teacher.img" />
            </div>
            <p class="teacher_first_line_name">{{teacher.name}}</p>
            <p class="teacher_first_line_state">{{teacher.state}}</p>
            <p class="teacher_second_line">{{teacher.text}}</p>
          </div>
        </div>
      </template>
    </div>
  </div>
</template>

<script>

import ArrowButton from "../../AdditionalComponents/ArrowButton.vue"

export default {
  methods: {
    multiItemSlider: function (selector, config) {
        this.mainElement = document.querySelector(selector); // основный элемент блока
        this.sliderWrapper = this.mainElement.querySelector('.teacher_blocks'); // обертка для .slider-item
        this.sliderItems = this.mainElement.querySelectorAll('.slider_teacher_block'); // элементы (.slider-item)
        this.sliderControls = document.querySelector('.teachers_label').querySelectorAll('.slider_arrow'); // элементы управления
        this.wrapperWidth = parseFloat(getComputedStyle(this.sliderWrapper).width); // ширина обёртки
        this.itemWidth = parseFloat(getComputedStyle(this.sliderItems[0]).width); // ширина одного элемента    
        this.step = this.itemWidth / this.wrapperWidth * 100; // величина шага (для трансформации)
        this.items = new Array();
        this.config = {
          isCycling: false, // автоматическая смена слайдов
          direction: 'right', // направление смены слайдов
          interval: 5000, // интервал между автоматической сменой слайдов
          pause: true // устанавливать ли паузу при поднесении курсора к слайдеру
        };

        for (let key in config) {
          if (key in this.config) {
            this.config[key] = config[key];
          }
        }

        // наполнение массива items
        this.sliderItems.forEach( (item, index) => {
          this.items.push({ item: item, position: index, transform: 0 });
        });

        // инициализация
        this.setUpListeners();
        this.cycle(this.config.direction);

        return {
          right: function () { // метод right
            this.transformItem('right');
          },
          left: function () { // метод left
            this.transformItem('left');
          },
          stop: function () { // метод stop
            this.config.isCycling = false;
            clearInterval(this.interval);
          },
          cycle: function () { // метод cycle 
            this.config.isCycling = true;
            clearInterval(this.interval);
            this.cycle();
          }
        }
    },

    // обработчик события click для кнопок "назад" и "вперед"
    controlClick: function (e) {
      if (e.target.classList.contains('slider_arrow')) {
        e.preventDefault();
        let direction = e.target.classList.contains('slider_arrow_right') ? 'right' : 'left';
        this.transformItem(direction);
        clearInterval(this.interval);
        this.cycle(this.config.direction);
      }
    },

    setUpListeners: function () {
      if (this.config.pause && this.config.isCycling) {
        this.mainElement.addEventListener('mouseenter', () => {
          clearInterval(this.interval);
        });
        this.mainElement.addEventListener('mouseleave', () => {
          clearInterval(this.interval);
          this.cycle(this.config.direction);
        });
      }
    },

    cycle: function (direction) {
      if (!this.config.isCycling) {
        return;
      }
      this.interval = setInterval( () => {
        this.transformItem(direction);
      }, this.config.interval);
    },

    getItemMin: function () {
      let indexItem = 0;
      this.items.forEach( (item, index) => {
        if (item.position < this.items[indexItem].position) {
          indexItem = index;
        }
      });
      return indexItem;
    },

    getItemMax: function () {
      let indexItem = 0;
      this.items.forEach( (item, index) => {
        if (item.position > this.items[indexItem].position) {
          indexItem = index;
        }
      });
      return indexItem;
    },

    getMin: function () {
      return this.items[this.getItemMin()].position;
    },

    getMax: function () {
      return this.items[this.getItemMax()].position;
    },

    transformItem: function (direction) {
      let nextItem;
      if (direction === 'right') {
        this.positionLeftItem++;
        if ((this.positionLeftItem + this.wrapperWidth / this.itemWidth - 1) > this.getMax()) {
          nextItem = this.getItemMin();
          this.items[nextItem].position = this.getMax() + 1;
          this.items[nextItem].transform += this.items.length * 100;
          this.items[nextItem].item.style.transform = 'translateX(' + this.items[nextItem].transform + '%)';
        }
        this.transform -= this.step;
      }
      if (direction === 'left') {
        this.positionLeftItem--;
        if (this.positionLeftItem < this.getMin()) {
          nextItem = this.getItemMax();
          this.items[nextItem].position = this.getMin() - 1;
          this.items[nextItem].transform -= this.items.length * 100;
          this.items[nextItem].item.style.transform = 'translateX(' + this.items[nextItem].transform + '%)';
        }
        this.transform += this.step;
      }
      this.sliderWrapper.style.transform = 'translateX(' + this.transform + '%)';
    }
  },

  mounted() {
    this.multiItemSlider('.teachers_slider', {
      isCycling: true
    })
  },
  name: 'TeachersComponent',
  components: { ArrowButton },
  data() {
    return {
      mainElement: null,
      sliderWrapper: null,
      sliderItems: null,
      sliderControls: null,
      wrapperWidth: null,
      itemWidth: null,
      positionLeftItem: 0,
      transform: 0,
      step: 0,
      items: new Array(),
      interval: 0,
      config: { isCycling: false, direction: 'right', interval: 5000, pause: true },
      teachersArrowButtonStyleFirst: { button: {'margin-left': '10px', 'margin-right': '10px'}, arrow: {'transform': 'rotate(135deg)', 'margin-right': '16px', 'margin-left': '18px'} },
      teachersArrowButtonStyleSecond: { button: {'margin-left': '10px', 'margin-right': '10px'}, arrow: {'transform': 'rotate(315deg)'} }
    }
  },
  props: {
    list: {
      type: Array,
      requierd: true
    }
  }
}
</script>

<style scoped>
.teachers_label {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin-left: 80px;
  margin-right: 80px;
}

.teachers_header {
  color: rgb(0, 0, 0);
  font-weight: 600;
  font-size: 24px;
  text-align: left;
  letter-spacing: 1px;
  word-spacing: 1px;
}

.teachers_slider {
  position: relative;
  overflow: hidden;
  margin-left: 80px;
  margin-right: 80px;
  margin-bottom: 60px;
}

.teacher_blocks { /*slider-wrapper*/
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  transition: transform 0.6s ease;
}

.slider_teacher_block {
  flex: 0 0 25%;
  max-width: 25%;
}

.teacher_block {
  display: grid;
  grid-template-columns: auto 66%;
  grid-template-rows: auto auto auto;
  margin-left: 20px;
  margin-right: 20px;
}

.teacher_first_line_icon {
  grid-row-start: 1;
  grid-row-end: 3;
  grid-column-start: 1;
  grid-column-end: 2;
  border-radius: 50%;
  width: 75px;
  height: 75px;
}

.teacher_first_line_icon_img {
  display: block;
  width: 100%;
  border-radius: 50%;
}

.teacher_first_line_name {
  text-align: left;
  margin-left: 3px;
  grid-row-start: 1;
  grid-row-end: 2;
  grid-column-start: 2;
  grid-column-end: 3;
  margin-bottom: 0px;
  font-size: 18px;
  font-weight: 600;
}

.teacher_first_line_state {
  text-align: left;
  margin-left: 3px;
  grid-row-start: 2;
  grid-row-end: 3;
  grid-column-start: 2;
  grid-column-end: 3;
  margin-top: 4px;
  font-size: 16px;
  color: rgb(185, 185, 185);
}

.teacher_second_line {
  grid-row-start: 3;
  grid-row-end: 4;
  grid-column-start: 1;
  grid-column-end: 3;
  text-align: justify;
  line-height: 150%;
}
</style>