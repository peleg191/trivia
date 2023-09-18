<template>
    <div class="game-body">
        <div class="question-title">
            Name The Flag
        </div>
        <div class="picture">
            <img class="image-class" :src="calcSource">
        </div>
        <div class="score">
            {{score}}
        </div>
        <div class="answers-body">
            <div class="answer-button" :class="answer1Class" @click="checkAnswer(1)">
                {{ answer1 }}
            </div>
            <div class="answer-button" :class="answer2Class" @click="checkAnswer(2)">
                {{ answer2 }}
            </div>
            <div class="answer-button" :class="answer3Class" @click="checkAnswer(3)">
                {{ answer3 }}
            </div>
            <div class="answer-button" :class="answer4Class" @click="checkAnswer(4)">
                {{ answer4 }}
            </div>
        </div>
    </div>
</template>
<script>
import flags from '../flags.js';
function getOtherIndeces(currentArray) {
    const originalArray = [1, 2, 3, 4];
    return originalArray.filter((x) => { return currentArray.indexOf(x) < 0 });
}
export default {
    name: 'main-game-component',
    data() {
        return {
            myFlags: flags,
            answer1: '',
            answer2: '',
            answer3: '',
            answer4: '',
            answer1Class: '',
            answer2Class: '',
            answer3Class: '',
            answer4Class: '',
            answerChosen: '',
            rightAnswer: '',
            rightAnswerIndex: 0,
            chosenQuestion: {},
            score:0
        }
    },
    methods: {
        newQuestion() {
            //choose question 
            const numOfQuestion = Math.round(Math.random() * this.myFlags.length);
            this.chosenQuestion = this.myFlags[numOfQuestion];
            this.rightAnswer = this.chosenQuestion.name;
            const randomNum = Math.round(Math.random() * 4) || 1;
            let indecesArray = [randomNum];
            this['answer' + randomNum] = this.rightAnswer;
            this.rightAnswerIndex = randomNum;
            this.myFlags.splice(numOfQuestion, 1);
            const otherRandomNum = Math.round(Math.random() * this.myFlags.length);
            const otherRandomIndexNum = getOtherIndeces(indecesArray)[0];
            indecesArray.push(otherRandomIndexNum);
            this['answer' + otherRandomIndexNum] = this.myFlags[otherRandomNum].name;
            const otherIndeces = getOtherIndeces(indecesArray);
            this['answer' + otherIndeces[0]] = this.myFlags[Math.round(Math.random() * this.myFlags.length)].name;
            this['answer' + otherIndeces[1]] = this.myFlags[Math.round(Math.random() * this.myFlags.length)].name;
        },
        checkAnswer(indexClicked) {
            if (indexClicked == this.rightAnswerIndex) {
                this['answer' + indexClicked + 'Class'] = 'correct-answer';
                this.score++;
                setTimeout(() => {
                    this['answer' + indexClicked + 'Class'] = '';
                    this.newQuestion();
                }, 1500)
            }
            else {
                this['answer' + indexClicked + 'Class'] = 'wrong-answer';
                setTimeout(() => {
                    this['answer' + indexClicked + 'Class'] = '';
                    this.newQuestion();
                }, 1500)
            }
        }
    },
    computed: {
        calcSource() {
            return this.chosenQuestion.flag;
        }
    },
    mounted() {
        this.newQuestion();
    }
}
</script>
<style scoped>
.game-body {
    height: 100vh;
    width: 100vw;
    background: #282828;
}
.score{
    height: 4vh;
    width: 4vh;
    font-size: 2vh;
    border-radius: 50%;
    background: darkviolet;
    color: white;
    position: absolute;
    text-align: center;
    line-height: 4vh;
    top: 12vh;
    left: 2vh;
}
.question-title {
    position: absolute;
    text-align: center;
    margin: 5vw 5vw 10vw 10vw;
    font-size: 5vh;
    color: black;
    width: 80vw;
    background: white;
    border-radius: 2vh;
}

.picture {
    margin-right: auto;
    margin-left: auto;
    padding-top: 20vh;
    width: 70vw;
    height: 20vh;
    display: flex;
    align-items: center;
    text-align: center;
}

.image-class {
    max-height: 25vh;
    margin-left: auto;
    margin-right: auto;
}

.answers-body {
    position: absolute;
    text-align: center;
    margin-left: auto;
    margin-right: auto;
    font-size: 5vh;
    color: white;
    margin-top: 5vh;
    width: 100vw;
    height: 80vh;
    margin-bottom: auto;
}

.answer-button {
    width: 75vw;
    margin-left: auto;
    margin-right: auto;
    border: 1px white;
    margin-top: 4vh;
    margin-bottom: 4vh;
    border-radius: 2vh;
}

/* .answer-button:hover {
    animation-name: answerButtonHoverAnimation;
    animation-duration: 1s;
    animation-fill-mode: forwards;
}

@keyframes answerButtonHoverAnimation {
    from {
        background: #282828;
        color: white;
    }

    to {
        background: white;
        color: black;
    }

} */

.correct-answer {
    animation-name: correctAnswer;
    animation-duration: 1.5s;
    animation-fill-mode: forwards;
    animation-iteration-count: 1;
}

@keyframes correctAnswer {
    from {
        background: inherit;
    }

    50% {
        background: #4BB543;
        color: white
    }

    to {
        background: #282828;
        color: white;
    }

}

.wrong-answer {
    animation-name: wrongAnswer;
    animation-duration: 1.5s;
    animation-fill-mode: forwards;
    animation-iteration-count: 1;
}

@keyframes wrongAnswer {
    from {
        background: inherit;
    }

    50% {
        background: #ff0033;
        color: white
    }

    to {
        background: #282828;
        color: white;
    }

}
</style>