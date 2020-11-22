<template>
  <div class="actual_label">
    <h4 class="actual_header">ВСЕ САМОЕ АКТУАЛЬНОЕ</h4>
    <div style="display: flex; flex-direction: row">
      <arrow-button :func="controlClick" direction="left" :style="actualArrowButtonStyleFirst"></arrow-button>
      <arrow-button :func="controlClick" direction="right" :style="actualArrowButtonStyleSecond"></arrow-button>
    </div>
  </div>
  <div class="actual_slider">
    <div class="actual_blocks">
      <template v-for="act in list" v-bind:key="act">
        <div class="slider_actual_block">
          <div class="actual_block">
            <div class="actual_first_line">
              <img class="actual_first_line_img" :src="act.img" />
            </div>
            <p class="actual_second_line">{{act.text}}</p>
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
        this.sliderWrapper = this.mainElement.querySelector('.actual_blocks'); // обертка для .slider-item
        this.sliderItems = this.mainElement.querySelectorAll('.slider_actual_block'); // элементы (.slider-item)
        this.sliderControls = document.querySelector('.actual_label').querySelectorAll('.slider_arrow'); // элементы управления
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
    this.multiItemSlider('.actual_slider', {
      isCycling: true
    })
  },
  name: 'ActualComponent',
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
      actualArrowButtonStyleFirst: { button: {'margin-left': '10px', 'margin-right': '10px'}, arrow: {'transform': 'rotate(135deg)', 'margin-right': '16px', 'margin-left': '18px'} },
      actualArrowButtonStyleSecond: { button: {'margin-left': '10px', 'margin-right': '10px'}, arrow: {'transform': 'rotate(315deg)'} }
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

<style>
.actual_label {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin-left: 80px;
  margin-right: 80px;
}

.actual_header {
  color: rgb(0, 0, 0);
  font-weight: 600;
  font-size: 24px;
  text-align: left;
  letter-spacing: 1px;
  word-spacing: 1px;
}

.actual_slider {
  position: relative;
  overflow: hidden;
  margin-left: 80px;
  margin-right: 80px;
  margin-bottom: 70px;
}

.slider_actual_block {
  flex: 0 0 33%;
  max-width: 33%;
}

.actual_blocks {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  transition: transform 0.6s ease;
}

.actual_block {
  display: grid;
  grid-template-columns: auto;
  grid-template-rows: auto auto;
  margin-left: 20px;
  margin-right: 20px;
}

.actual_first_line {
  border-radius: 9px/9px;
  box-shadow: 4px 4px 9px 0 rgb(211, 211, 211);
  width: auto;
  padding-top: 20px;
  padding-bottom: 40px;
  padding-right: 15%;
  padding-left: 15%;
  height: 260px;
}

.actual_first_line_img {
  display: block;
  border-radius: 9px/9px;
  width:100%;
  height: 100%;
}

.actual_second_line {
  text-align: center;
  margin: auto;
  font-size: 16px;
  width: 65%;
  margin-top: 20px;
}
</style>