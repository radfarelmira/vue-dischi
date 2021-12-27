<template>
    <header>
        <div class="logo">
            <img src="../assets/img/logo.png" alt="logo">
        </div>  
    </header>
</template>

<script>
export default {
    name: 'Header',
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

header{
    background-color: $primary-color;

    .logo{
        padding: 10px 20px;
        img{
            width: 50px;
        }
    }

}
</style>