<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Here / คลิกที่นี่ {{delay}}</div>
  <h1 v-if="update">Data Update</h1>
</template>

<script>
export default {
    props:['delay'],
    data(){
        return{
            showBlock:false,
            update:false,
            score:0,
            timer:null,
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showBlock=true;
            this.startTimmer()
        }, this.delay)
    },
    updated(){
        setTimeout(()=>{
            this.update=true;     
        },1000);

       
    },
    methods:{
        startTimmer(){
            this.timer=setInterval(()=>{
                this.score+=50;
            },50);
        },
        stopTimer(){
            clearInterval(this.timer);
            this.$emit('endGame',this.score);
            
        }
    }

}
</script>

<style>
.block{
    background-color: rgb(104, 110, 203);
    width: 350px;
    height: 200px;
    margin: 20px auto;
    padding-top: 30px;
    border: 2px solid red;
    border-radius: 20px;
}

</style>