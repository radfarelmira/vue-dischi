<template>

<div class="gif-image">
    <img src="https://i.gifer.com/VAyR.gif" alt="gif">
</div>
   
</template>

<script>
export default {
    name: 'Loader',
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

.gif-image{
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    img{
        width: 100px;
    }
    
}


</style>