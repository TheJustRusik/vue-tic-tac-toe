<script setup>
// import HelloWorld from './components/Component1.vue'
// import Btn from './components/Button.vue'
    import { ref, registerRuntimeCompiler } from 'vue';

    let p1 = ref('x')
    let p2 = ref('o')
    let curr_que = p1

    let errors = ref(["You are trying to make a move that already has a piece on it!",
                      ""])

    let field = ref([[' ',' ',' '],
                     [' ',' ',' '],
                     [' ',' ',' ']])

    function checkWinner(field) {
        for (let i = 0; i < 3; i++){
            if (field[i][0] === field[i][1] && field[i][1] === field[i][2] && field[i][1] !== ' '){
                return field[i][0];
            }
        }
        for (let i = 0; i < 3; i++){
            if (field[0][i] === field[1][i] && field[1][i] === field[2][i] && field[0][i] !== ' '){
                return field[0][i];
            } 
        }
        if (field[0][0] === field[1][1] && field[1][1] === field[2][2] && field[0][0] !== ' '){
            return field[0][0]
        }
        if (field[0][2] === field[1][1] && field[1][1] === field[2][0] && field[0][2] !== ' '){
            return field[0][2]
        }
        return "null";
    }

    function click(x,y){
        if (field.value[x][y] != ' '){
            return
        }
        field.value[x][y] = curr_que.value
        
        if (checkWinner(field.value) !== 'null'){
            
        }

        curr_que = curr_que == p1 ? p2 : p1
    }


</script>

<template>
    <div class="mx-4">
        <div class="flex justify-center">
            <h1 class="bg-gradient-to-r from-sky-500 to-pink-500 text-transparent bg-clip-text font-extrabold text-4xl m-4">Tic Tac Toe</h1>
        </div>
        <div class="grid lg:grid-cols-2">
            <div class="">
                <div class="flex">
                    <p class="text-sky-300 text-2xl font-extrabold">Player 1:</p>
                    <input maxlength="1" v-model="p1" type="text" class="bg-transparent text-white text-2xl font-extrabold">
                </div>
                <div class="flex">
                    <p class="text-pink-300 text-2xl font-extrabold">Player 2:</p>
                    <input maxlength="1" v-model="p2" type="text" class="w-5 bg-transparent text-white text-2xl font-extrabold">
                </div>
            </div>
            <div>
                <div class="flex justify-center mb-4">
                    <div>
                        <p v-if="curr_que == p1" class="text-white text-xl text-sky-300">It's the first player's turn ({{ p1 }})</p>
                        <p v-else class="text-white text-xl text-pink-300">It's the second player's turn ({{ p2 }})</p>
                    </div>
                </div>
                <div class="flex justify-center">
                    <div style="white-space: pre-wrap;">

                        <div class="flex border-b border-sky-500">
                            <button @click="click(0,0)">
                                <div class="border-r text-white p-4 text-8xl border-sky-500">
                                    <p style="width: 1em; height: 1em;" class="text-center">{{ field[0][0] }}</p>
                                </div>
                            </button>
                            <button @click="click(0,1)">
                                <div class="border-r text-white p-4 text-8xl border-sky-500">
                                    <p style="width: 1em; height: 1em;" class="text-center">{{ field[0][1] }}</p>
                                </div>
                            </button>
                            <button @click="click(0,2)">
                                <div class="text-white p-4 text-8xl">
                                    <p style="width: 1em; height: 1em;" class="text-center">{{ field[0][2] }}</p>
                                </div>
                            </button>
                        </div>

                        <div class="flex border-b  border-sky-500 border-sky-500">
                            <button @click="click(1,0)">
                                <div class="border-r text-white p-4 text-8xl border-sky-500">
                                    <p style="width: 1em; height: 1em;" class="text-center">{{ field[1][0] }}</p>
                                </div>
                            </button>
                            <button @click="click(1,1)">
                                <div class="border-r text-white p-4 text-8xl border-sky-500">
                                    <p style="width: 1em; height: 1em;" class="text-center">{{ field[1][1] }}</p>
                                </div>
                            </button>
                            <button @click="click(1,2)">
                                <div class="text-white p-4 text-8xl">
                                    <p style="width: 1em; height: 1em;" class="text-center">{{ field[1][2] }}</p>
                                </div>
                            </button>
                        </div>

                        <div class="flex">
                            <button @click="click(2,0)">
                                <div class="border-r text-white p-4 text-8xl border-sky-500">
                                    <p style="width: 1em; height: 1em;" class="text-center">{{ field[2][0] }}</p>
                                </div>
                            </button>
                            <button @click="click(2,1)">
                                <div class="border-r text-white p-4 text-8xl border-sky-500">
                                    <p style="width: 1em; height: 1em;" class="text-center">{{ field[2][1] }}</p>
                                </div>
                            </button>
                            <button @click="click(2,2)">
                                <div class="text-white p-4 text-8xl">
                                    <p style="width: 1em; height: 1em;" class="text-center">{{ field[2][2] }}</p>
                                </div>
                            </button>
                        </div>
                        
                    </div>
                    
                </div>
            </div>
        </div>
    </div>
</template>
