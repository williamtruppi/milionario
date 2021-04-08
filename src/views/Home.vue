<template>
  <div class="home">
     <Container />
     <Welcome />
     <Quiz />
  </div>
</template>

<script>
// @ is an alias to /src
import Container from "@/components/Container.vue";
import Quiz from "@/components/Quiz.vue";
import Welcome from '../components/Welcome.vue';

export default {
  name: "Home",
  components: {
    Container,
    Quiz,
    Welcome,
  },
};
</script>

<style lang="scss" scoped>
  .home{
    height: 100%;
  }
</style>
