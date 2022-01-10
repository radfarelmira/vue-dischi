<template>
    <div class="select-container">
        <select @change="selectDone" v-model="selectValue" name="" id="">
            <option value="">All Genre</option>
            <option value="Pop">Pop</option>
            <option value="Rock">Rock</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'GenreSelect',
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
    margin: 10px 0;
    select{
        width: 200px;
        font-weight: bold;
    }
}

</style>