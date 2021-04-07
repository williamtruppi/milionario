<template>
    <div class="quiz">
        <div class="question">
            <h2>{{this.quizList[index].question}}</h2>
        </div>
        <div class="answers">
            <div class="answer-box"  v-for="(quiz, i) in quizList[index].answers" :key="i">
                <h2 id="answer" @click="answerResult(i)">{{quiz.value}}</h2>
            </div>
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
                    },
                    {
                        question: "Miglior giocatore di Basket",
                        answers: [
                            {value: "Magally", correct: false},
                            {value: "Berlusconi", correct: false},
                            {value: "Jordan", correct: true},
                            {value: "Enrico Mentana", correct: false}
                        ]
                    },
                    {
                        question: "Pattern Laravel",
                        answers: [
                            {value: "MCC", correct: false},
                            {value: "Cvc", correct: false},
                            {value: "MVC", correct: true},
                            {value: "SVP", correct: false}
                        ]
                    }
                ]
            }  
        },

        methods: {
            randomQuestion() {
                this.index = Math.floor(Math.random() * (this.quizList.length));
            },

            answerResult(i){
                let answers = document.querySelectorAll('#answer');
                if ((this.quizList[this.index].answers[i].correct === true)){
                    answers[i].style.backgroundColor = "green";
                }
            }
        },

        mounted() {
            /* console.log(this.quizList); */
            this.randomQuestion();
        }
        
    }

</script>


<style scoped lang="scss">

    .right-answer{background-color: green;}
    .wrong-answer{background-color: red;}

    .quiz{
        color: white;
        background-color: #11093A;
        padding: 2% 0;

        .question{
            display: flex;
            justify-content: center;
                h2{
                    width: fit-content;
                    border: 1px solid white;
                    padding: 1% 8%;
                }
        }

        .answers{
            display: flex; 
            flex-wrap: wrap; 
            
            .answer-box{
                margin-top: 2%;
                min-width: 50%;
                text-align: center;
                display: flex;
                justify-content: center;

                h2{
                    width: fit-content;
                    border: 1px solid white;
                    padding: 1% 8%;
                    cursor: pointer;
                }
            }
           
        }
    } 
    
</style>