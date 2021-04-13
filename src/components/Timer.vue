<template>
    <div>
        
        <a class="timerBtn" href="#" @click="toggleTimer">
            <b-button class="timerBtn" v-if="!isRunning" variant="primary">
                {{ time }}
                <b-icon icon="alarm"></b-icon>
            </b-button>
            <b-button class="timerBtn" v-if="isRunning" variant="warning">
                {{ time }}
                <b-icon icon="alarm" animation="fade"></b-icon>
            </b-button>
        </a>
        <div v-if="time > 0">
            <b-button @click="resetTime" variant="danger"><b-icon icon="arrow-counterclockwise"></b-icon></b-button>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['order'],
        data() {
            return {
                time: this.order,
                isRunning: false,
                interval: undefined // store the interval here
            }
        },
        methods: {
            toggleTimer() {

                if (this.isRunning) {
                    clearInterval(this.interval);
                    console.log('timer stops');
                   
                } else {
                    this.interval = setInterval(this.incrementTime, 1000);
                    console.log('timer starts');
                }
                this.isRunning = !this.isRunning; // better to read
            },
            incrementTime() {
                this.time = parseInt(this.time) + 1;
            },
            resetTime(){
                this.time = 0;
                if(this.isRunning) {
                    clearInterval(this.interval);
                    this.isRunning = false;
                }
            }
        }
    }
</script>
<style scoped>
    .timerBtn{
        display: flex;
        align-items: center;
        justify-content: center;
        width:100%;
    }
</style>