<template>
    <section>
        <div class="container">
            <GenreSelect @selectClicked="selectPerformed"/>

            <ArtistSelect @selectClicked="selectPerformed"/>

            <div class="wrapper">
                <div v-if="!isLoadingApi" class="row row-cols-2 row-cols-lg-6">
                    <DiscCard v-for="(disc, index) in filteredDiscs" :key="index" :discObj="disc"/>  
                </div>

            <Loader v-else/>
        </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import DiscCard from './DiscCard';
import Loader from './Loader';
import GenreSelect from './GenreSelect';
import ArtistSelect from './ArtistSelect';

export default {
    name: 'DiscList',
    components: {
        DiscCard,
        Loader,
        GenreSelect,
        ArtistSelect
    },
    data: function () {
    return {
      discs: [],
      isLoadingApi: true,
      selectValue: ''
    };
  },
  methods: {
      selectPerformed: function (text) {
          this.selectValue= text;
        },
    },
  computed: {
      filteredDiscs: function() {
        if (this.selectValue === '') {
            return this.discs;
        }

        const filteredArray = this.discs.filter((element) => {
            if (element.genre === this.selectValue){
                return element.genre;
            }else if (element.author === this.selectValue){
                return element.author;
            }

            });

            return filteredArray;
        }
    },
  created: function () {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then((response) => {
      this.discs = response.data.response;

      this.isLoadingApi= false;
    });
  }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

section{
    background-color: #1e2d3b;
    padding: $section-padding;
    .wrapper{
        display: flex;
        justify-content: center;
        align-items: flex-start;
        min-height: calc(100vh - 100px);
        .row{
            display: flex;
            justify-content: center;
        }
    }
}

</style>