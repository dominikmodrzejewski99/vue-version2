<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Quiz Wins"/>
    <QuestionComponent/>
  </div>
</template>

<script>
// @ is an alias to /src
import QuestionComponent from '@/components/QuestionComponent.vue';

export default {
  name: 'HomeView',
  components: {
    QuestionComponent,
  }
}
</script>
