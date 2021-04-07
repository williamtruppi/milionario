<template>
    <div class="quiz">
        <div class="question" style="text-align: center;">
            <h2 v-for="quiz in quizList" :key="quiz.question">{{quiz.question}}</h2>
        </div>
        <div class="answers" style="display: flex; flex-wrap: wrap; text-align: center;">
            <h2 v-for="(quiz, i) in quizList[index].answers" :key="i" style="min-width: 50%;">{{quiz.value}}</h2>
        </div>
    </div>
</template>

<script>

    export default {

        data() {
            return {
                color: "red",
                index: 0,
                quizList: [
                    {
                        question: "Il numero di maglia di delpiero",
                        answers: [
                            {value: "10", correct: true},
                            {value: "99", correct: false},
                            {value: "69", correct: false},
                            {value: "00", correct: false}
                        ]
                    }
                ]
            }  
        },

        mounted() {
            console.log(this.quizList);
        }
        
    }

</script>


<style scoped lang="scss">

    .quiz{
        color: white;
    }
    
</style>