<template>
  <main>
    <h4 class="sub_header">ЗАЧЕМ НУЖЕН АНГЛИЙСКИЙ ЯЗЫК</h4>
    <ul class="for_what_list">
      <template v-for="item in forWhatList" v-bind:key="item">
        <for-what-component :text="item.text" :title="item.label" :img="item.img"></for-what-component>
      </template>
    </ul>
    <h4 class="sub_header">НЕМНОГО О WINDSOR</h4>
    <div class="about_block">
      <template v-for="item in aboutWindsorList" v-bind:key="item">
        <about-windsor :color="item.color" :label="item.label" :text="item.text"></about-windsor>
      </template>
    </div>
    <div class="how_to_start_label">
      <h4 class="sub_header" style="margin-top: 20px; margin-bottom: 20px;">КАК НАЧАТЬ ОБУЧЕНИЕ</h4>
      <colorful-button :style="howToStartButtonStyle"  text="Хочу пройти курс"></colorful-button>
    </div>
    <div class="canvas_block">
      <canvas-component></canvas-component>
    </div>
    <h4 class="sub_header">ВАРИАНТЫ ОБУЧЕНИЯ</h4>
    <div class="variants_block">
      <template v-for="item in variantsList" v-bind:key="item">
        <education-variant :label="item.label" :sublabel="item.sublabel" :text="item.text" :oldprice="item.oldprice" :price="item.price"></education-variant>
      </template>
    </div>
    <online-test></online-test>
    <h4 class="sub_header">ПОЧЕМУ WINDSOR</h4>
    <windsor-advantages></windsor-advantages>
    <doubt-component></doubt-component>
    <div class="how_to_start_label">
      <h4 class="sub_header">С WINDSOR ВЫ ДОСТИГНЕТЕ УСПЕХА</h4>
      <colorful-button :style="howToStartButtonStyle" text="Хочу пройти курс"></colorful-button>
    </div>
    <success-component :img="successImg"></success-component>
    <teachers-component :list="teachersList"></teachers-component>
    <actual-component :list="actualList"></actual-component>
    <h4 class="sub_header">ИСТОРИИ УСПЕХА С WINDSOR</h4>
    <stories-component :callback="this.callbackFunction" :list="storiesList" :icon="youtubeImg"></stories-component>
    <want-to-learn-component></want-to-learn-component>
    <h4 style="margin-left:80px;" class="actual_header">КАК НАЙТИ WINDSOR</h4>
    <map-component></map-component>
  </main>
</template>

<script>
import ForWhatComponent from "./ForWhatComponent.vue"
import AboutWindsor from "./AboutWindsor.vue"
import CanvasComponent from "./CanvasComponent.vue"
import EducationVariant from "./EducationVariant.vue"
import OnlineTest from "./OnlineTest.vue"
import WindsorAdvantages from "./WindsorAdvantages.vue"
import DoubtComponent from "./DoubtComponent.vue"
import SuccessComponent from "./SuccessComponent.vue"
import TeachersComponent from "./SlidersComponents/TeachersComponent.vue"
import ActualComponent from "./SlidersComponents/ActualComponent.vue"
import StoriesComponent from "./SlidersComponents/StoriesComponent.vue"
import WantToLearnComponent from "./WantToLearnComponent.vue"
import MapComponent from "./MapComponent.vue"
import ColorfulButton from "./../AdditionalComponents/ColorfulButton.vue"

import first from "../../assets/first.png"
import second from "../../assets/second.png"
import third from "../../assets/third.png"
import success from "../../assets/success.png"

import jack from "../../assets/jack.png";
import daniel from "../../assets/daniel.png";
import danny from "../../assets/danny.png";
import alina from "../../assets/alina.png";

import seminar from "../../assets/seminar.png";
import seminar2 from "../../assets/seminar2.png";
import lesson from "../../assets/lesson.png";

import elena from "../../assets/elena.png";
import kate from "../../assets/kate.png";
import sofia from "../../assets/sofia.png";

import icon from "../../assets/youtube.png";

export default {
    name: 'Main',
    components: {
      ForWhatComponent, AboutWindsor, CanvasComponent, EducationVariant,
      OnlineTest, WindsorAdvantages, DoubtComponent, SuccessComponent,
      TeachersComponent, ActualComponent, StoriesComponent, WantToLearnComponent,
      MapComponent, ColorfulButton
    },
    data() {
      return {
        howToStartButtonStyle: {
          'padding': '15px 30px 15px 30px',
          'color': 'white',
          'background-color': 'rgb(235, 38, 78)',
          'box-shadow': '0px 4px 6px 0px rgba(224, 78, 107, 0.7)',
          'border-style': 'none',
          'margin-right': '80px'
        },
        forWhatList: [
          {label: "Повышенная заработная плата", text: "В России зарплата специалистов, владеющих иностранным языком, выше на 30%", img: first},
          {label: "Передвижение по всему миру", text: "Вы сможете легко передвигаться в любую точку мира, легко общаясь с иностранцами", img: second},
          {label: "Расширение кругозора", text: "Отличный способ личностного развития при помощи изучения иностранного языка", img: third}
        ],
        aboutWindsorList: [
          {color: "rgb(28, 23, 109)", label: "МЕТОДИКА ОБУЧЕНИЯ", text: "Обучение взрослых проходит по уникальной методике, - Lexical Approach. По результатам исследований способность говорить вырабатывается в случаях, когда человек имеет большой объем слов и фраз. В основе - изучение словосочетаний, фраз и выражений в контексте и активное их использование."},
          {color: "rgb(51, 51, 245)", label: "ИНДИВИДУАЛЬНЫЙ ПОДХОД", text: "За счет того, что группы небольшие и отбираются по определенным параметрам, программа обучения готовится для каждой группы индивидульно. Что это значит на практике? Что преподаватель будет готовить и давать на уроках те материалы, которые важны и интересны именно вам."}
        ],
        variantsList: [
          {label: "ДЛЯ НАЧИНАЮЩИХ", sublabel: "Занятия в группах от 6 человек", text: "Курс основан на профессиональном подходе, оптимальной технологии обучения, которая направлена на практическое применение знаний.", price: "9900 руб."},
          {label: "ПОДГОТОВКА К IELTS", sublabel: "Минимальный уровень владения языком: High Intermediate", text: "Тщательное изучение формата экзамена; изучение эффективных стратегий выполнения заданий; разбор верных решений и ошибок в выполннении заданий.", oldprice: "25 200", price: "24 350 руб. до 16 июля"},
          {label: "ИНДИВИДУАЛЬНО", sublabel: "Занятия в офисе или по Skype", text: "Быстрое освоение материала, так как такие занятия создают лучшие условия для преодоления смущения при попытке использования речи.", price: "2300 руб./час"}
        ],
        teachersList: [
          {name: "JACK", state: "США", text: '"My favorite thing about teaching is making connections. Linking bits of informations to create an intellectual picture is rewarding and entertaining"', img: jack},
          {name: "DANIEL", state: "Великобритания", text: '"I enjoy seeing students delve into a topic and be really passionate about giving their thoughts while putting into practice the important language skills."', img: daniel},
          {name: "DANNY", state: "Новая Зеландия", text: '"I have a passion for sharing knowledge and believe there is no greater satisfaction than having a positive impact on the lives of others."', img: danny},
          {name: "ALINA", state: "Россия", text: '"Убеждена, что изучение нового языка является отпрвной точкой в саморазвитиии, "узнавании" себя и следовании своим мечтам."', img: alina},
          {name: "ALINA2", state: "Россия", text: '"Убеждена, что изучение нового языка является отпрвной точкой в саморазвитиии, "узнавании" себя и следовании своим мечтам."', img: alina},
          {name: "ALINA3", state: "Россия", text: '"Убеждена, что изучение нового языка является отпрвной точкой в саморазвитиии, "узнавании" себя и следовании своим мечтам."', img: alina},
        ],
        actualList: [
          {text: 'Бесплатные семинары "Как преодолеть языковой барьер"', img: seminar},
          {text: '53-я Международная Конференция IATEFL 2019 в Ливерпуле', img: seminar2},
          {text: 'Открытый урок в парке Москвы с носителями языка', img: lesson},
          {text: '54-я Международная Конференция IATEFL 2020 в Ливерпуле', img: seminar2},
          {text: '2-й Открытый урок в парке Москвы с носителями языка', img: lesson}
        ],
        storiesList: [
          {name: "Елена Бычкова", label: "Подготовка к IELTS", text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. ", img: elena, isSelected: false},
          {name: "Екатерина Ситникова", label: "Подготовка к IELTS", text: "Курс мне помогли подобрать с учетом моего уровняи целей, и в итоге он полностью соответствовал и тому, и другому. Я узнала многое о структуре эссе, получила полезные советы по распределению времени на экзамене, научилась быстро просматривать тексты.", img: kate, isSelected: true},
          {name: "София Устимчук", label: "Подготовка к IELTS", text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.", img: sofia, isSelected: false},
          {name: "Kate", label: "Подготовка к IELTS", text: "Курс мне помогли подобрать с учетом моего уровняи целей, и в итоге он полностью соответствовал и тому, и другому. Я узнала многое о структуре эссе, получила полезные советы по распределению времени на экзамене, научилась быстро просматривать тексты.", img: kate, isSelected: false},
          {name: "Sofia", label: "Подготовка к IELTS", text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.", img: sofia, isSelected: false},
        ],
        successImg: success,
        youtubeImg: icon
      }
    },
    methods: {
      callbackFunction: function(index) {
        this.storiesList[index].isSelected = !this.storiesList[index].isSelected;
      }
    }
}
</script>

<style>
.for_what_list {
  display: flex;
  flex-direction: row;
  margin-left: 80px;
  padding: 0px;
}

.about_block {
  display: flex;
  flex-direction: row;
  justify-content: center;
  color: rgb(28, 23, 109);
  margin-bottom: 80px;
}

.canvas_block {
  margin-right: 80px;
  margin-left: 60px;
  margin-bottom: 80px;
}

.variants_block {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 70px;
}

.how_to_start_label {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.test_label {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
</style>