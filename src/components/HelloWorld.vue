<template>
  <div class="question">
    <p class="paragraph">Pytanie {{question}}</p>
    <div id="a" class="question-content">
      {{questions.question}}
    </div>

    <div  class="question-box">
      <div :class="{ background: isBackground }" @click="toggleColor" class="question-answer">
        {{questions.answer_a}}
      </div>
    </div>
    <div class="question-box">
      <div class="question-answer">
        {{questions.answer_b}}
      </div>
    </div>
    <div class="question-box">
      <div class="question-answer">
        {{questions.answer_c}}
      </div>
    </div>
    <div class="question-box">
      <div class="question-answer">
        {{questions.answer_d}}
      </div>
    </div>
    <button @click="handleBtn" class="btn">wyślij</button>
  </div>
</template>
<script>

export default {
  name: 'QuestionComponent',
  data() {
    return {
      questions: [],
      question: 2,
      isBackground: true,
      font: {
        weight: 800,
      },
    };
  },
  methods: {
    handleBtn() {

    },
    toggleColor() {
      console.log(event.target.id)
      this.isBackground = !this.isBackground;
    }
  },
  mounted() {
    fetch(`http://127.0.0.1:8000/api/question/${this.question}`)
        .then(response => response.json())
        .then(data => this.questions = data)
        .catch(err => console.error(err.message))
  },
  components: {},

  props: {
    numberQuestions: Number,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.question {
  width: 100%;
  height: 80%;
  background: white;

  .paragraph {
    font-weight: 700;
    font-size: 30px;
    padding-top: 60px;
  }

  &-content {
    padding-top: 30px;
  }

  .question-box {
    display: flex;
    justify-content: center;
    height: 100px;
    .question-answer {
      margin-top: 50px;
      border-radius: 30px;
      width: 70%;
      border: 1px dashed red;
    }
  }

  .btn {
    cursor: pointer;
    width: 100px;
    height: 40px;
    color: whitesmoke;
    border: none;
    border-radius: 20px;
    background: #1f23b1;
    margin-top: 20px
  }

  .background {
    background: #42b983;
  }



}
</style>
