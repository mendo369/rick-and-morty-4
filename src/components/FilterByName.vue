<template>
  <div class="search">
      <input type="text"
      placeholder="Search by name"
      v-model="name"
      @keyup="filter()"
      >
  </div>
</template>

<script>
import {ref} from 'vue'
import {useStore} from 'vuex'
export default {
    setup(){
        const store = useStore()
        const name = ref('')

        const filter =()=>{
            store.dispatch('filterByName', name.value)
        }

        return{
            name,
            filter
        }
    }
}
</script>

<style lang="scss">
:root{
    --width-search: 400px;
}
.search{
    width: var(--width-search);
    margin: 3rem auto 0;
    input{
        height: 53px;
        width: var(--width-search);
        border: none;
        border-radius: 10px;
        padding: 0 0.5rem;
    }
}
@media(max-width: 460px){
    :root{
        --width-search: 100%;
    }
}
</style>