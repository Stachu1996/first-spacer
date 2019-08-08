<template>
    <div class="search">
      <input 
        name='search' 
        id='search' 
        v-model='searchValue' 
        @input='handleInput'
      />
    </div>
</template>

<script>
export default {
    name: 'Search',
}
</script>

<style lang='scss' scoped>
    .search {
        margin-top: 50px;

        display: flex;
        flex-direction: column;
        width: 300px;

        label {
            font-family: Montserrat, sans-serif;
        }

        input{
            height: 30px;
            border: 0;
            border-bottom: 1px solid white;

            background: rgba($color: #000000, $alpha: 0)
        }
    }
</style>
