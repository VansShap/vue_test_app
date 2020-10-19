<template>
  <div class = "test_label">
    <h4 class = "sub_header">НЕ ЗНАЮ, КАКОЙ КУРС ВЫБРАТЬ</h4>
    <div class = "test_dot_box">
      <p class = "test_dot" v-bind:class = "{test_dot_selected: currentQuestion === 0}"  @click = "previous">01</p>
      <p class = "test_dot"></p>
      <p class = "test_dot" v-bind:class = "{test_dot_selected: currentQuestion !== 0 && currentQuestion !== 9 }">{{isValid() ? '0' + (currentQuestion + 1): ''}}</p>
      <p class = "test_dot"></p>
      <p class = "test_dot" v-bind:class = "{test_dot_selected: currentQuestion === 9}" @click = "next">10</p>
    </div>
  </div>
  <p class = "test_sublabel">Определите уровень своего английского с помощью онлайн мини-теста</p>
  <div class = "question_box">
    <p class = "question">{{selectedQuestion.question}}</p>
    <div class = "question_select">
      <div class = "select_head">{{selectedQuestion.selectedVariant}} <p @click = "dropList" class="select_arrow" v-bind:class = "{select_arrow_active: isDropped}"></p></div>
      <div class = "select_item" v-bind:class = "{select_item_active: isDropped}" v-for = "variant in selectedQuestion.variants" v-bind:key = "variant" @click="selectItem(variant)">{{variant}}</div>
    </div>
    <button class = "question_button">Посмотреть результат</button>
  </div>
</template>

<script>
export default {
    name: "OnlineTest",
    data() {
      return {
        isDropped: false,
        currentQuestion: 0,
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
    methods: {/*
      mounted() {
        console.log("dsagdsag");
        this.selectedQuestion = this.questionList[0];
      },*/

      dropList: function() {
        this.isDropped = !this.isDropped;

      },

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
      },

      selectItem: function(variant) {
        this.selectedQuestion.selectedVariant = variant;
        this.isDropped = false;
      }
    }
}
</script>

<style>
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
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-size: 16px;
  font-weight: 500;
  user-select: none;
}

.test_sublabel {
  width: 20%;
  text-align: left;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
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
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-size: 16px;
  color: black;
  font-weight: 500;
  align-self: baseline;
}

.question_button {
  height: 50px;
  border-radius: 9px/9px;
  padding: 15px 40px 15px 40px;
  color: rgb(235, 38, 78);
  border-color: rgb(235, 38, 78);
  border-width: 1px;
  background-color: white;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-size: 16px;
  font-weight: 500;
  display: block;
  cursor: pointer;
  align-self: baseline;
}

.question_button:focus {
  outline: none;
}

.question_select {
  width: 25%;
  display: flex;
  flex-direction: column;
  background-color: transparent;
}

.select_head {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-size: 15px;
  padding-bottom: 4px;
  color: rgb(185, 185, 185);
  border-bottom-color: black;
  border-bottom-width: 1px;
  border-bottom-style: solid;
}

.select_item {
  display: none;
}

.select_item_active {
  display: block;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-size: 15px;
  padding-top: 8px;
  padding-bottom: 8px;
  background-color:  rgb(202, 202, 202);
  border-bottom-color: rgb(168, 168, 168);
  border-bottom-width: 1px;
  border-bottom-style: solid;
}

.select_item_active:hover {
  background-color:  rgba(202, 202, 202, 0.5);
  color: rgba(0, 0, 0, 0.5);
  cursor: pointer;
}

.select_arrow {
  display: inline-block;
  border: solid black;
  border-width: 0 1px 1px 0;
  display: inline-block;
  padding: 3px;
  transform: rotate(45deg);
  cursor: pointer;
}

.select_arrow:hover, .select_arrow_active:hover{
  border: solid  rgb(185, 185, 185);
  border-width: 0 1px 1px 0;
}

.select_arrow_active {
  transform: rotate(-135deg);
}

</style>