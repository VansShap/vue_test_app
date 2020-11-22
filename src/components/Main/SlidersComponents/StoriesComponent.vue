<template>
<div class="story_slider"> 
  <div class="story_blocks">
    <template v-for="story in list" v-bind:key="story">
      <div class="block slider_block">
      <template v-if="story.isSelected">
        <div class="selected_story_slider_block">
          <div class="selected_story_block">
            <div class="selected_story_icon">
              <img class="selected_story_icon_img" :src="story.img" />
            </div>
            <div class="selected_story_form">
              <p class="selected_story_name">{{story.name}}</p>
              <p class="selected_story_label">{{story.label}}</p>
              <p class="selected_story_text">{{story.text}}</p>
              <div class="selected_story_youtube">
                <img class="selected_story_youtube_img" :src="icon">
              </div>
            </div>
            <div class="selected_story_arrows">
              <arrow-button :func="controlClick" direction="left" :style="storiesArrowButtonStyleFirst"></arrow-button>
              <arrow-button :func="controlClick" direction="right" :style="storiesArrowButtonStyleSecond"></arrow-button>
            </div>
          </div>
        </div>
      </template>

      <template v-else>
        <div class="story_slider_block">
          <div class="story_block">
            <div class="story_block_icon">
              <img class="story_block_icon_img" :src="story.img" />
            </div>
            <p class="story_block_name">{{story.name}}</p>
            <p class="story_block_label">{{story.label}}</p>
          </div>
        </div>
      </template>
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
        this.sliderWrapper = this.mainElement.querySelector('.story_blocks'); // обертка для .slider-item
        this.sliderItems = this.mainElement.querySelectorAll('.slider_block'); // элементы (.slider-item)
        this.sliderControls = document.querySelector('.selected_story_arrows').querySelectorAll('.slider_arrow'); // элементы управления
        this.wrapperWidth = parseFloat(getComputedStyle(this.sliderWrapper).width); // ширина обёртки
        this.itemWidth = parseFloat(getComputedStyle(this.sliderItems[0]).width); // ширина одного элемента    
        this.step = this.itemWidth / this.wrapperWidth * 100; // величина шага (для трансформации)
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
          this.items.push({ item: item, position: index, transform: 0, itemIndex: index });
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

        if (this.selectedItem <= this.items.length - 2) {
          this.selectedItem++;
        }
        else {
          this.selectedItem = 0;
        }
        this.callback(this.selectedItem, this.items);
        if (this.selectedItem === 0) {
          this.callback(this.items.length - 1, this.items);
        }
        else {
          this.callback(this.selectedItem - 1, this.items);
        }
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
        if (this.selectedItem > 0) {
          this.selectedItem--;
        }
        else {
          this.selectedItem = this.items.length - 1;
        }
        this.callback(this.selectedItem, this.items);
        if (this.selectedItem === this.items.length - 1) {
          this.callback(0, this.items);
        }
        else {
          this.callback(this.selectedItem + 1, this.items);
        }
      }
      this.sliderWrapper.style.transform = 'translateX(' + this.transform + '%)';
    }
  },

  mounted() {
    this.multiItemSlider('.story_slider', {
      isCycling: true
    });
  },

  name: "StoriesComponent",
  components: { ArrowButton },
  data() {
    return {
      mainElement: null,
      sliderWrapper: null,
      sliderItems: new Array(),
      sliderControls: null,
      wrapperWidth: null,
      itemWidth: null,
      positionLeftItem: 0,
      transform: 0,
      step: 0,
      items: new Array(),
      interval: 0,
      selectedItem: 1,
      config: { isCycling: false, direction: 'right', interval: 5000, pause: true },
      storiesArrowButtonStyleFirst: { button: {'margin-left': '10px', 'margin-right': '10px'}, arrow: {'transform': 'rotate(135deg)', 'margin-right': '16px', 'margin-left': '18px'} },
      storiesArrowButtonStyleSecond: { button: {'margin-left': '10px', 'margin-right': '10px'}, arrow: {'transform': 'rotate(315deg)'} }
    }
  },
  props: {
    list: {
      type: Array,
      requierd: true
    },
    icon: {
      type: String,
      requierd: true
    },
    callback: {
      type: Function,
      required: true
    },
    trans: {
      type: String
    }
  }
}
</script>

<style>
.story_slider {
  position: relative;
  overflow: hidden;
  margin-left: 80px;
  margin-right: 80px;
  height: 360px;
}

.story_blocks {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  transition: transform 0.6s ease;
}

.slider_block {
  flex: 0 0 33%;
  max-width: 33%;
}

.selected_slider_block {
  flex: 0 0 50%;
  max-width: 50%;
}

.selected_story_block {
  position: relative;
  margin-left: 5%;
  box-shadow: 4px 4px 9px 0 rgb(211, 211, 211);
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

.selected_story_youtube {
  height: 22px;
  width: 30px;
  margin-left: auto;
  margin-right: 0px;
}

.selected_story_youtube_img {
  display: block;
  width: 100%;
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
  bottom: -5%;
  left: 40%;
  display: flex;
  flex-direction: row;
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
  width: 100%;
  border-radius: 50%;
}
</style>