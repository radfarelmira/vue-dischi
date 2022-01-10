<template>
    <div class="select-container">
        <select @change="selectDone" v-model="selectValue" name="" id="">
            <option value="">All Artists</option>
            <option value="Bon Jovi">Bon Jovi</option>
            <option value="Sting">Sting</option>
            <option value="Steve Gadd Band">Steve Gadd Band</option>
            <option value="Eric Clapton">Eric Clapton</option>
            <option value="Metallica">Metallica</option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'ArtistSelect',
    data: function () {
        return {
            selectValue: ''
        };
    },
    methods: {
        selectDone: function () {
            this.$emit('selectClicked', this.selectValue)
        }
    }
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

.select-container{

    select{
        width: 200px;
        font-weight: bold;
    }
}

</style>