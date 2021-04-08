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
            <button @click="nextQst()">NEXT</button>
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
                answers: [],
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
                this.answers = document.querySelectorAll('#answer');
                if ((this.quizList[this.index].answers[i].correct === true)){
                    this.correctAnswers++;
                    this.answers[i].style.backgroundColor = "green";
                    //disabilito il pulsante per evitare click successivi
                    this.answers[i].disabled = true;
                    //elimino le risposte residue
                    for(let y=0; y < this.answers.length; y++){
                        if(y !== i) {
                            this.answers[y].disabled = true;
                            this.answers[y].style.backgroundColor = 'red';
                        }
                    }
                } else {
                    this.wrongAnswers++;
                    this.answers[i].style.backgroundColor = "red";
                    //disabilito il pulsante per evitare click successivi
                    this.answers[i].disabled = true;
                    //elimino le risposte residue
                    for(let j=0; j < this.answers.length; j++){
                        if(j !== i) {
                            this.answers[j].disabled = true;
                            this.answers[j].style.backgroundColor = 'grey';
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
                
                // se le lunghezze dei due array sono diverse, eseguo il codice
                if (this.selectedQuestions.length !== this.quizList.length){

                    // genero un numero casuale finché questo non è diverso rispetto a quello presente nella dom già fatte
                    let tempRnd = 0;
                    do {
                        tempRnd = Math.floor(Math.random() * (this.quizList.length));
                    } while (this.selectedQuestions.includes(tempRnd));

                    //passo id domanda univoca al suo array e la stampo a schermo
                    this.index = tempRnd;
                    this.selectedQuestions.push(this.index);

                    //riabilito pulsanti e rendo trasparenti gli sfondi
                    this.answers.forEach(elem => {
                        elem.disabled = false;
                        elem.style.backgroundColor = 'transparent';
                    });

                    //resetto il messaggio di errore
                    this.correctMsg = "";
                }

                console.log(this.selectedQuestions);
                console.log("Risposte corrette " + this.correctAnswers);
                console.log("Risposte sbagliate " + this.wrongAnswers);
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
        height: calc(100% - 250px);
        color: white;
        background-color: #11093A;
        padding: 2% 0;
        text-align: center;
        display: none;

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