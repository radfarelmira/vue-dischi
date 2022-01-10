<template>
    <section>
        <div class="container">
            <DiscSelect @selectClicked="selectPerformed"/>

            <div class="wrapper">
                <div v-if="!isLoadingApi" class="row row-cols-2 row-cols-lg-6">
                    <DiscCard v-for="(disc, index) in discs" :key="index" :discObj="disc"/>  
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
import DiscSelect from './DiscSelect';

export default {
    name: 'DiscList',
    components: {
        DiscCard,
        Loader,
        DiscSelect
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
        align-items: center;
        min-height: calc(100vh - 100px);
        .row{
            display: flex;
            justify-content: center;
        }
    }
}

</style>