<template>
    <div>
        <h2>SabeloTudo</h2>
        <p>
            Pregunte por si/no:
            <input v-model="question" type="text" />
            <button v-on:click="nuevo">Nueva</button>
        </p>
        <h3>{{ answer }} !</h3>
        <img v-bind:src="image" />
    </div>
</template>

<script>
    import axios from "axios";

    export default {
        // Properties keep track of
        data() {
            return {
                question: "",
                answer:
                    "no le puedo dar respuesta hasta que no haga una pregunta",
                image: "",
            };
        },
        watch: {
            question: function(newVal, oldVal) {
                const vm = this;
                vm.answer = "esperando hasta q pare de tipear.";

                setTimeout(function() {
                    vm.getAnswer();
                }, 350);
            },
        },

        // App methods
        methods: {
            getAnswer: function() {
                const vm = this;

                if (!vm.question.includes("?")) {
                    vm.answer =
                        "Las preguntas terminan con un signo de interrogación";
                    vm.image = "";
                    return;
                }
                vm.answer = "Pensando...";

                setTimeout(function() {
                    axios.get("https://yesno.wtf/api").then(function(response) {
                        vm.answer = response.data.answer;
                        vm.image = response.data.image;
                    });
                }, 500);
            },

            nuevo: function() {
                this.question = "";
            },
        },
    };
</script>

<style scoped>


    p {
        color: rgb(93, 93, 93);
        font-size: 18px;
    }
    input {
        font-size: 18px;
    }
    button {
        height: 34px;
    }
</style>
