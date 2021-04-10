<template>
    <div class="endgame">
        <h1 v-if="fromCorrect">Risposte corrette: {{fromCorrect}}</h1>
        <h1 v-if="fromWrong">Risposte sbagliate: {{fromWrong}}</h1>
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

<style lang="scss" scoped>
        .endgame{
            height: calc(100% - 250px);
            display: none;
            color: white;
            align-items: center;
            justify-content: space-around;
            flex-direction: column;

            h1{
                width: fit-content;
            }
        }
</style>