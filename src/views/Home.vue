<template>
  <div class="home">
     <Container />
     <Welcome />
     <Quiz />
     <Endgame />
  </div>
</template>

<script>
// @ is an alias to /src
import Container from "@/components/Container.vue";
import Quiz from "@/components/Quiz.vue";
import Welcome from '../components/Welcome.vue';
import Endgame from "@/components/Endgame.vue";

export default {
  name: "Home",
  components: {
    Container,
    Quiz,
    Welcome,
    Endgame
  },
};
</script>

<style lang="scss" scoped>
  .home{
    height: 100%;
  }
</style>
