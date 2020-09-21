<template>
  <div id="app" class="text-center">
     <button @click="countdown(3)" class="btn bt-cool">3 seg</button>
     <button @click="countdown(60)" class="btn bt-cool">1 min</button>
     <button @click="countdown(300)" class="btn bt-cool">5 min</button>
     <button @click="countdown(600)" class="btn bt-cool">10 min</button>
     <button @click="countdown(1800)" class="btn bt-cool">30 min</button>
     <h1 class="pt-3">{{time}}</h1>
  </div>
</template>

<script>
let interval;
  export default {
    name: "Contador",
    data() {
      return {
        time: "00:00",
      };
    },
    methods:{
        countdown(sec){
            clearInterval(interval);
            const now = Date.now();
            const end = now + (sec + 1) * 1000;
            this.discount(end);
        },
        discount (end){
             interval = setInterval(()=>{
                const leftTime = parseInt(Math.round((end - Date.now())/ 1000)) ; //Se convierte a enterno evitando negativos
                if (leftTime < 0){
                    clearInterval(interval);
                    return;
                }
                const minutes = Math.floor((leftTime % 3600)/ 60)
                const seconds = leftTime % 60;
                console.log(minutes, seconds)


                if (String(seconds).length === 1 && String(minutes).length === 1) {
                 this.time = `0${minutes}:0${seconds}`;
                } else if (
                String(seconds).length === 1 &&
                String(minutes).length != 1
                ) {
                this.time = `${minutes}:0${seconds}`;
                } else if (
                String(seconds).length != 1 &&
                String(minutes).length === 1
                ) {
                this.time = `0${minutes}:${seconds}`;
                } else {
                this.time = `${minutes}:${seconds}`;
                }
            }, 1000)
        }
    }
  }
</script>

<style scoped>
  .bt-cool{
    color: lightseagreen;
    background-color: darkorchid;
    border-color: darkmagenta;
  }

  .bt-cool:hover{
    background-color:darkmagenta;
  }
</style>