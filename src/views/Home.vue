<template>
  <div class="wrapper">
    <Claim />
    <Search />
    
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim';
import Search from '@/components/Search';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'home',
  components : {
    Claim, Search,
  },
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: debounce( function() {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error)
        });
    }, 500),
  },
};

</script>

<style lang="scss" scoped>

  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    width: 100%;
    height: 100vh;
    padding: 30px;
    margin: 0;

    background-image: url('../assets/background.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 00% 0%;
  }


</style>
