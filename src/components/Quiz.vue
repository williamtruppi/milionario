<template>
    <div class="quiz">
        <div class="question">
            <h2>{{this.quizList[index].question}}</h2>
        </div>
        <div class="answers">
            <div class="answer-box"  v-for="(quiz, i) in quizList[index].answers" :key="i">
                <button id="answer" @click="answerResult(i)">{{quiz.value}}</button>
            </div>
        </div>

        <h1>{{this.correctMsg}}</h1>

        <div class="buttons-quiz">
            <button>NEXT</button>
        </div>
    </div>
</template>

<script>

    export default {

        data() {
            return {
                correctMsg: "",
                correctAnswers: 0,
                wrongAnswers: 0,
                index: 0,
                selectedQuestions: [],
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
                    },
                     {
                        question: "Ed io sono...",
                        answers: [
                            {value: "Cap America", correct: false},
                            {value: "Iron Man", correct: true},
                            {value: "Posaman", correct: false},
                            {value: "Magally", correct: false}
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
                console.log("ciao");
                let answers = document.querySelectorAll('#answer');
                if ((this.quizList[this.index].answers[i].correct === true)){
                    this.correctAnswers++;
                    answers[i].style.backgroundColor = "green";
                    //disabilito il pulsante per evitare click successivi
                    answers[i].disabled = true;
                    //elimino le risposte residue
                    for(let y=0; y < answers.length; y++){
                        if(y !== i) {
                            answers[y].disabled = true;
                            answers[y].style.backgroundColor = 'red';
                        }
                    }
                } else {
                    this.wrongAnswers++;
                    answers[i].style.backgroundColor = "red";
                    //disabilito il pulsante per evitare click successivi
                    answers[i].disabled = true;
                    //elimino le risposte residue
                    for(let j=0; j < answers.length; j++){
                        if(j !== i) {
                            answers[j].disabled = true;
                            answers[j].style.backgroundColor = 'grey';
                        } else {
                            answers[i].style.backgroundColor = "green";
                        }
                    }

                    //mostro un messaggio con la risposta corretta
                    this.quizList[this.index].answers.forEach(elem => {
                        if(elem.correct === true){
                            this.correctMsg = "La risposta corretta è " + elem.value;
                        }
                    });
                    
                }
            },

            nextQst(){
                let tempRnd = Math.floor(Math.random() * (this.quizList.length));
                if (!(this.selectedQuestions.includes(tempRnd))){
                    this.index = tempRnd;
                }
            }
        },

        mounted() {
            this.randomQuestion();
            this.selectedQuestions.push(this.index);
        }
        
    }

</script>


<style scoped lang="scss">

    .quiz{
        color: white;
        background-color: #11093A;
        padding: 2% 0;
        text-align: center;

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

                #answer{
                    background-color: transparent;
                    width: fit-content;
                    color: white;
                    border: 1px solid white;
                    padding: 1% 8%;
                    cursor: pointer;
                }
            }
           
        }
    } 
    
</style>