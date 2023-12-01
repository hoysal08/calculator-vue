<template>
    <div class="calculator">
        <div class="input-area">
            <input class="result" type="text" v-model="expression" />
        </div>
        <div class="button-grid">
            <button @click="addToExpression('7')">7</button>
            <button @click="addToExpression('8')">8</button>
            <button @click="addToExpression('9')">9</button>
            <button class="operator" @click="addToExpression('+')">+</button>
            <button @click="addToExpression('4')">4</button>
            <button @click="addToExpression('5')">5</button>
            <button @click="addToExpression('6')">6</button>
            <button @click="addToExpression('-')">-</button>
            <button @click="addToExpression('1')">1</button>
            <button @click="addToExpression('2')">2</button>
            <button @click="addToExpression('3')">3</button>
            <button @click="addToExpression('**')">^</button>
            <button class="equal" @click="calculateResponse()">=</button>
            <button @click="addToExpression('0')">0</button>
            <button @click="addToExpression('.')">.</button>
            <button class="clear" @click="clearExpression()">C</button>
            <button @click="addToExpression('*')">*</button>
            <button @click="addToExpression('/')">/</button>
            <button class="backspace" @click="backspace()">&#9003;</button> <!-- Backspace button -->
        </div>
    </div>
</template>
  
<script>
import { ref } from "vue";

export default {
    setup() {
        const expression = ref("");
        const addToExpression = (value) => {
            expression.value += value;
        };

        const clearExpression = () => {
            expression.value = "";
        };

        const backspace = () => {
            expression.value = expression.value.slice(0, -1);
        };

        const calculateResponse = () => {
            try {
                const result = eval(expression.value);
                expression.value = result.toString();
            } catch (error) {
                expression.value = "Error";
            }
        };

        const handleKeyDown = (event) => {
            if (event.key === "Enter") {
                calculateResponse();
            }
        }

            return {
                expression,
                addToExpression,
                clearExpression,
                calculateResponse,
                backspace,
                handleKeyDown
            };
        },
    }
</script>
  
<style scoped>
.calculator {
    max-width: 400px;
    margin: 0 auto;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    background-color: #f0f0f0;
}

.input-area {
    text-align: right;
    padding: 10px;
}

.result {
    width: 100%;
    font-size: 24px;
    border: none;
    outline: none;
    background: none;
}

.button-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
}

button {
    padding: 10px;
    font-size: 18px;
    border: none;
    background-color: #f5f5f5;
    cursor: pointer;
    transition: background-color 0.2s;
}

button:hover {
    background-color: #ddd;
}

.equal {
    grid-column: span 2;
    background-color: #ffa726;
    color: white;
}

.clear {
    background-color: #e57373;
    color: white;
}

button:active {
    transform: translateY(2px);
}
</style>
  