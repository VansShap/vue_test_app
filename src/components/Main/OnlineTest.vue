<template>
  <div class="test_label">
    <h4 class="sub_header">НЕ ЗНАЮ, КАКОЙ КУРС ВЫБРАТЬ</h4>
    <div class="test_dot_box">
      <p class="test_dot" v-bind:class="{test_dot_selected: currentQuestion === 0}"  @click="previous">01</p>
      <p class="test_dot"></p>
      <p class="test_dot" v-bind:class="{test_dot_selected: currentQuestion !== 0 && currentQuestion !== 9 }">{{isValid() ? '0' + (currentQuestion + 1): ''}}</p>
      <p class="test_dot"></p>
      <p class="test_dot" v-bind:class="{test_dot_selected: currentQuestion === 9}" @click="next">10</p>
    </div>
  </div>
  <p class="test_sublabel">Определите уровень своего английского с помощью онлайн мини-теста</p>
  <div class="question_box">
    <p class="question">{{selectedQuestion.question}}</p>
    <div class="question_select">
      <custom-select :firstVariant="selectedQuestion.selectedVariant" :variants="selectedQuestion.variants"></custom-select>
    </div>
    <colorful-button :style="onlineTestButtonStyle" text="Посмотреть результат"></colorful-button>
  </div>
</template>

<script>
import ColorfulButton from "./../AdditionalComponents/ColorfulButton.vue"
import CustomSelect from "./../AdditionalComponents/CustomSelect.vue"

export default {
    name: "OnlineTest",
    components: {
      ColorfulButton, CustomSelect
    },
    data() {
      return {
        currentQuestion: 0,
        onlineTestButtonStyle: {
          'padding': '15px 40px 15px 40px',
          'color': 'rgb(235, 38, 78)',
          'border-color': 'rgb(235, 38, 78)',
          'border-width': '1px',
          'background-color': 'white', 
          'font-weight': '500',
          'align-self': 'baseline'
        },
        questionList: [
          {question: "1George ...... to work hard but he does now.", variants: ["doesn't want", "enjoys", "hates", "???"], selectedVariant: "Варианты ответа"},
          {question: "2George ...... to work hard but he does now.", variants: ["doesn't want", "enjoys", "hates", "???"], selectedVariant: "Варианты ответа"},
          {question: "3George ...... to work hard but he does now.", variants: ["doesn't want", "enjoys", "hates", "???"], selectedVariant: "Варианты ответа"},
          {question: "4George ...... to work hard but he does now.", variants: ["doesn't want", "enjoys", "hates", "???"], selectedVariant: "Варианты ответа"},
          {question: "5George ...... to work hard but he does now.", variants: ["doesn't want", "enjoys", "hates", "???"], selectedVariant: "Варианты ответа"},
          {question: "6George ...... to work hard but he does now.", variants: ["doesn't want", "enjoys", "hates", "???"], selectedVariant: "Варианты ответа"},
          {question: "7George ...... to work hard but he does now.", variants: ["doesn't want", "enjoys", "hates", "???"], selectedVariant: "Варианты ответа"},
          {question: "8George ...... to work hard but he does now.", variants: ["doesn't want", "enjoys", "hates", "???"], selectedVariant: "Варианты ответа"},
          {question: "9George ...... to work hard but he does now.", variants: ["doesn't want", "enjoys", "hates", "???"], selectedVariant: "Варианты ответа"},
          {question: "10George ...... to work hard but he does now.", variants: ["doesn't want", "enjoys", "hates", "???"], selectedVariant: "Варианты ответа"}
        ],
        selectedQuestion: {question: "1George ...... to work hard but he does now.", variants: ["doesn't want", "enjoys", "hates", "???"], selectedVariant: "Варианты ответа"}
      }
    },
    methods: {
      previous: function() {
        this.currentQuestion === 0 ? this.currentQuestion = 9 : this.currentQuestion = this.currentQuestion - 1;
        this.selectedQuestion = this.questionList[this.currentQuestion];
      },

      next: function() {
        this.currentQuestion === 9 ? this.currentQuestion = 0 : this.currentQuestion = this.currentQuestion + 1;
        this.selectedQuestion = this.questionList[this.currentQuestion];
      },

      isValid: function() {
        if (this.currentQuestion >= 1 && this.currentQuestion <= 8)
          return true;
        else return false;          
      }
    }
}
</script>

<style scoped>
.test_dot {
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

.test_dot_selected {
  text-shadow: 1px 1px 2px rgba(224, 78, 107, 0.7);
  color: crimson;
  font-size: 18px;
  border-radius: initial;
  background-color: initial;
  width: initial;
  height: initial;
  cursor: pointer;
}

.test_dot:first-child, .test_dot:last-child {
  border-radius: initial;
  background-color: initial;
  width: initial;
  height: initial;
  cursor: pointer;
}

.test_dot_box {
  margin-right: 80px;
  font-size: 16px;
  font-weight: 500;
  user-select: none;
}

.test_sublabel {
  width: 20%;
  text-align: left;
  margin-left: 80px;
  font-weight: 600;
  font-size: 16px;
  line-height: 150%;
}

.question_box {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-direction: row;
  margin-left: 80px;
  margin-right: 80px;
  margin-bottom: 60px;
}

.question {
  font-size: 16px;
  color: black;
  font-weight: 500;
  align-self: baseline;
}

.question_select {
  width: 25%;
  align-self: flex-start;
  display: flex;
  flex-direction: column;
  background-color: transparent;
  position: relative;
}
</style>