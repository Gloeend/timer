<script>
import ButtonComponent from "./components/button-component/button-component.vue";

export default {
  data() {
    return {
      timer: 0,
      active: false
    }
  },
  components: {ButtonComponent},
  methods: {
    timerEvent() {
      if (this.timer) {
        return;
      }
      // this.timer = 120000;
      this.timer = 2000;
      setInterval(() => this.active = true, this.timer)
    }
  },
  watch: {
    timer(value) {
      if (value === 0) {
        return;
      }
      new Promise(res => setTimeout(() => this.timer -= 1000, 1000))
    }
  },
  computed: {
    minutes() {
      let minutes = this.timer > 0 ? Math.floor(this.timer / 1000 / 60) % 60 : 0;
      let seconds = this.timer > 0 ? Math.floor(this.timer / 1000) % 60 : 0;

      minutes = minutes < 10 ? "0" + minutes : minutes;
      seconds = seconds < 10 ? "0" + seconds : seconds;

      return minutes + ":" + seconds;
    }
  }
}

</script>

<template>
  <button-component @click="timerEvent">
    <div class="content">
      <span class="text">{{ active ? "Отправить повторно" : "Отправить сообщение" }}</span>
      <span class="timer" v-if="timer">{{ minutes }}</span>
    </div>
  </button-component>
  <a class="link" href="https://google.com">Не помню пароль</a>
</template>

<style scoped>
.content {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.text, .timer {
  display: block;
}

.text {
  font-size: 1.25rem;
  line-height: 1.5rem;
}

.timer {
  background: #C4250E;
  border-radius: 0.3125rem;
  font-size: 0.8125rem;
  margin-left: .75rem;
  line-height: 1rem;
  padding: .25rem;
}

.link {
  color: #FF6E00;
  font-size: 1.25rem;
  transition: 250ms ease-out all;
}

.link:hover {
  background: linear-gradient(90deg, #D7650F 0%, #E1250A 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-fill-color: transparent;
  text-shadow: 0px 8px 24px rgba(215, 101, 15, 0.7);
}
</style>
