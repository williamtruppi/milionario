<template>
    <div class="welcome">
       <h1>Benvenuta/o nell'unico quiz capace di farti diventare MILIONARIO!</h1>
       <button @click="startGame()">INIZIA LA TUA SCALATA</button>
    </div>
</template>

<script>
    export default {
        data: function () {
            return {
                count: 0
            }
        },

        methods: {

            startGame() {
                document.querySelector('.quiz').style.display = "block";
                document.querySelector('.welcome').style.display = 'none';
            }
        }
    }
</script>

<style lang="scss" scoped>
    .welcome{
        height: calc(100% - 250px);
        text-align: center;
        color: white;
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        flex-direction: column;

        button{
            width: fit-content;
        }
    }
</style>