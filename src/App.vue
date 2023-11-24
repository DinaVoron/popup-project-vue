<script>
export default {
  data() {
    return {
      visible: false,
      visibleInfo: false,
      info: [
        {title: "name", value: ''},
        {title: "phone", value: ''},
        {title: "email", value: ''},
        {title: "work", value: ''},
        {title: "accept", value: false}
      ]
    }
  },
  methods: {
    showPopup() {
      this.visible = !this.visible;
    },
    removePopup() {
      this.visible = !this.visible;
    },
    sendInfo() {
      this.visible = !this.visible;
      this.visibleInfo = true;
    }
  }
}
  
</script>

<template>
  <div id="popupWin" class="popup" v-if="visible">
    <h1>Хотите себе такой же попап?</h1>
    <p>Оставьте ваши данные</p>
    <form name="popupForm">
        <div class ="mainFlex">
            <div class="flex">
                <div class ="inputFlex">
                    <label>
                        Имя:<br>
                        <input type="text" v-model="info[0].value" name="name">
                    </label>
                    <label>
                        Телефон:<br>
                        <input type="text" v-model="info[1].value" name="phone">
                    </label>
                    <label>
                        Email:<br>
                        <input type="text" v-model="info[2].value" name="email">
                    </label>
                </div>
            </div>
            <div class="flex">
                <label>
                    Компания:<br>
                    <input type="text" v-model="info[3].value" name ="work">
                </label>
                <label>
                    Согласие на обработку данных:
                    <input type="checkbox" v-model="info[4].value" name="accept">
                </label>
            </div> 
        </div>
        <div class ="buttonFlex">
            <button type="button" id="popupSend" v-on:click="sendInfo">Отправить</button>
        </div>
    </form>
</div>
<div class="blackBack" id="black" v-if="visible" v-on:click="removePopup"></div>
<div class="formDiv">
    <form>
        <button type="button" id="popupButton" v-on:click="showPopup" v-if="!visibleInfo">Начать</button>
    </form>
    <div id="valueDiv" v-if="visibleInfo">
      <p v-for="inf in info">
        {{inf.title}}: {{inf.value}}
      </p>
    </div>
</div>
</template>

<style>


#app {
  height: 100%;
}

@import './assets/main.css';
</style>
