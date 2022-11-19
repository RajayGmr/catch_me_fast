<template>
    <p>Result is - {{gamescore}} ms</p>
    <p>ผลลัพธ์คือ - {{gamescore}} ms</p>
    <div v-if="gamescore<250" class="fast">
        <p>You are too fast</p>
        <p>คุณเร็วเกินไป</p>
    </div>
    <div v-else-if="gamescore>250 && gamescore<500" class="good">
        <p>You are good</p>
        <p>คุณเก่งนะ</p>
    </div>
    <div v-else class="late">
        <p>You are too late</p>
        <p>คุณสายเกินไป</p>
    </div>
    
  
</template>

<script>
export default {
    props:['gamescore']

}
</script>

<style>
.fast{
    color: green;
    font-family: 'Courier New', Courier, monospace;
    font-size: large;
}
.good{
    color: rgb(0, 34, 255);
    font-family: 'Courier New', Courier, monospace;
    font-size: large;
}
.late{
    color: red;
    font-family: 'Courier New', Courier, monospace;
    font-size: large;
}

</style>