<script>

export default {
    data() {
        return {
            answer: Math.floor(Math.random() * (100 - 1) + 1),
            input: 0,
            gg: "-",
            title: "猜數字",
            min: 1,
            max: 100,
            changMin: (this.input < this.answer && this.input > this.min),
            changMax: (this.input > this.answer && this.input < this.max),
            victory: this.input == this.answer
        }
    },
    methods: {
        guess() {
            if (this.input == this.answer) {
                this.min = null;
                this.max = null;
                this.gg = "猜到ㄌ";
                this.title = "猜數字";
                this.input = null;
            }
            else if (this.input < this.answer && this.input > this.min) {
                this.min = this.input;
                this.title = "猜數字";
                this.input = null;
            }
            else if (this.input > this.answer && this.input < this.max) {
                this.max = this.input;
                this.title = "猜數字";
                this.input = null;
            }
            else {
                this.title = "請輸入範圍內的數字"
                this.input = null;
            }

        }

    },
    mounted() {

    }

}
</script>

<template>

    <div class="field2">
        <h1>{{ title }}</h1>
        <div class="field3">
            <p>{{ min }}</p>
            <p>{{ gg }}</p>
            <p>{{ max }}</p>
        </div>
        <input type="number" v-model="input">
        <button type="button" @click="guess">回答</button>
    </div>
</template>

<style lang="scss" scoped>
.field2 {
    position: relative;
    height: 400px;
    width: 350px;
    display: flex;
    flex-direction: column;
    border-radius: 8px;
    align-items: center;
    background-color: white;
    margin:auto;
    justify-content: space-around;
    top: 13vh;


    .field3 {
        display: flex;
        justify-content: space-around;
        font-size: 40px;
        font-weight: 500;

        p {
            margin: 0 30px;
        }
    }

    button {
        background-color: gray;
        color: white;
        border: none;
        padding: 4px 16px;
        border-radius: 8px;
        &:hover{
            transition: 0.2s;
            color: red;
            background-color: black;
            transform: scale(1.1);

        }
        &:active{
            transform: scale(0.9);
        }
    }
}
</style>