<template>
  <div class="home">
     <Container />
     <Quiz />
  </div>
</template>

<script>
// @ is an alias to /src
import Container from "@/components/Container.vue";
import Quiz from "@/components/Quiz.vue";

export default {
  name: "Home",
  components: {
    Container,
    Quiz,
  },
};
</script>
