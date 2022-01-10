<template>
    <div class="disc text-center">
        <div class="disc-image">
            <img :src="discObj.poster" :alt="discObj.title">
        </div>

        <h3 class="disc-title">{{discObj.title}}</h3>

        <div class="disc-author">{{discObj.author}}</div>

        <div class="disc-year">{{discObj.year}}</div>
    </div>
</template>

<script>
export default {
    name: 'DiscCard',
    props: {
        discObj: Object
    }
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

.disc{
    background-color: $primary-color;
    margin: 10px;
    padding: 20px;
    min-height: 450px;

    &-image{
        height: 200px;
        overflow: hidden;

        img{
            height: 100%;
            object-fit: cover;
        }
    }



    &-title{
        color: white;
        margin-top: 10px;
        text-transform: uppercase;
        font-weight: bold;
        font-size: 20px;
    }

    &-author{
        color: $secondary-color;
        margin-top: 10px;
        font-weight: bold;
    }

    &-year{
        color: $secondary-color;
        font-weight: bold;
    }



}

</style>