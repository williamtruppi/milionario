<template>
    <div class="endgame">
        <div v-if="fromCorrect" class="mt-3 alert alert-secondary" >Risposte corrette: {{fromCorrect}}</div>
        <div v-if="fromWrong" class="mt-3 alert alert-secondary" >Risposte sbagliate: {{fromWrong}}</div>
    </div>
</template>

<script>
    import {eventBus} from "../main";
    export default {
        data() {
            return {
                counter: 0,
                fromCorrect: 0,
                fromWrong: 0,
            }
        },

        created() {
            eventBus.$on('eventCorrectAnswers', (message) => {
                this.fromCorrect = message;
            });

            eventBus.$on('eventWrongAnswers', (message) => {
                this.fromWrong = message;
            });
        }
    };
</script>