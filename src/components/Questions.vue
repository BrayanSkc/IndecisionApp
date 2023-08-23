
<template>
  <img v-if="image" :src="image" />
  <div class="bg-dark" />
  <div class="indecision-container">
    <input type="text" name="question" id="quesion" placeholder="Hazme una pregunta" v-model="question">
    <p>Recuerda terminar con un signo de interrogación</p>

    <div>
      <h2>{{ oldQuestion }}</h2>
      <h1>{{ answer }}</h1>
    </div>

  </div>
</template>

<script>

export default {
  data() {
    return { question: this.question, answer: null, image: '', oldQuestion: null }
  },
  methods: {
    async getAnswer() {
      this.answer = 'Pensando...'
      const data = await fetch('https://yesno.wtf/api').then(res => res.json());
      this.image = data.image
      this.answer = data.answer
      this.oldQuestion= this.question
    },

  },
  watch: {
    question(value, oldValue) {

      if (!value.endsWith('?')) return
      this.getAnswer()
    }
  }

}
</script>

<style scoped>
img,
.bg-dark {
  height: 100vh;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
}

.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
}

.indecision-container {
  position: relative;
  z-index: 99;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
  font-size: 18px;
  font-weight: 600;
}

input:focus {
  outline: none;
}

p {
  color: white;
  font-size: 20px;
  margin-top: 20px;
}

h1,
h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}
</style>