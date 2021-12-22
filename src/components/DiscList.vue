<template>
    <section>
        <div class="container">
            <div v-if="discs.length > 0" class="row row-cols-2 row-cols-lg-6">
                <DiscCard v-for="(disc, index) in discs" :key="index" :discObj="disc"/>  
            </div>

            <Loader v-else/>
        </div>

    </section>
</template>

<script>
import axios from 'axios';
import DiscCard from './DiscCard';
import Loader from './Loader';

export default {
    name: 'DiscList',
    components: {
        DiscCard,
        Loader,
    },
    data: function () {
    return {
      discs: [],
    };
  },
  created: function () {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then((response) => {
      this.discs = response.data.response;
    });
  }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

section{
    background-color: #1e2d3b;
    padding: $section-padding;
    .container{
        
        .row{
            display: flex;
            justify-content: center;
        }
    }
}

</style>