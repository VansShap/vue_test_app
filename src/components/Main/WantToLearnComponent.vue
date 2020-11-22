<template>
  <div class="want_to_learn_block">
    <p class="want_to_learn_label">ХОЧУ ОБУЧАТЬСЯ В WINDSOR</p>
    <p class="want_to_learn_text">Оставьте заявку прямо сейчас и получите гарантированную скидку на любой из курсов</p>
    <form class="want_to_learn_form">
      <p class="want_to_learn_form_label">ВВЕДИТЕ ВАШИ ДАННЫЕ</p>
      <p class="want_to_learn_form_sublabel">Наш консультант перезвонит Вам в течении 10 минут</p>
      <input class="want_to_learn_form_input" placeholder="Имя" /><br/>
      <input class="want_to_learn_form_input" type="email" placeholder="E-mail"/><br/>
      <input class="want_to_learn_form_input" type="tel" placeholder="Телефон"/><br/>
      <colorful-button :style="wantToLearnButtonStyle" text="Оставить заявку"></colorful-button>
    </form>
  </div>
</template>

<script>
import ColorfulButton from "./../AdditionalComponents/ColorfulButton.vue"

export default {
  name: "WantToLearnComponent",
  components: {
    ColorfulButton
  },
  data() {
    return {
      wantToLearnButtonStyle: { 
        'width': '80%', 
        'padding': '15px 30px 15px 30px', 
        'margin-top': '40px', 
        'margin-bottom': '40px', 
        'margin-right': 'auto', 
        'margin-left': 'auto', 
        'color': 'white', 
        'background-color': 'rgb(235, 38, 78)', 
        'box-shadow': '0px 4px 6px 0px rgba(224, 78, 107, 0.7)', 
        'border-style': 'none', 
        'align-self': 'center' 
      }
    }
  }
}
</script>

<style>
.want_to_learn_block {
  position: relative;
  padding: 5% 8% 5% 8%;
  background-color: rgb(59, 144, 255);
  color: white;
  text-align: left;
  margin-bottom: 100px;
}

.want_to_learn_label {
  font-weight: 600;
  font-size: 24px;
  letter-spacing: 1px;
}

.want_to_learn_text {
  width: 40%;
  font-weight: 500;
  font-size: 18px;
}

.want_to_learn_form {
  width: 40%;
  position: absolute;
  text-align: center;
  right: 3%;
  top: -20%;
  box-shadow: 4px 4px 9px 0 rgb(211, 211, 211);
  background-color: white;
  color: black;
  z-index: 10;
}

.want_to_learn_form_label {
  margin-top: 7%;
  margin-bottom: 0%;
  font-size: 18px;
  font-weight: 600;
  margin-left: auto;
  margin-right: auto;
}

.want_to_learn_form_sublabel {
  margin-top: 2%;
  width: 35%;
  margin-left: auto;
  margin-right: auto;
  font-size: 15px;
  color: rgb(71, 71, 71);
}

.want_to_learn_form_input {
  width: 80%;
  margin-left: auto;
  margin-right: auto;
  padding: 20px 0px 15px 5px;
  outline: 0;
  border: none;
  border-bottom: 1px solid rgb(71, 71, 71);
}
</style>