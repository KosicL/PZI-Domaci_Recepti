<template>
  <div>
   <ShowCard v-if="recept" :recept="recept" />
  </div>
</template>

<script>
import axios from 'axios';
import accountStore from '@/composables/accountStore'; 
import ShowCard from '@/components/ShowCard'; 

export default {
  data() {
    return {
      recept: null
    };
  },
  created() {
    this.fetchRecept();
  },
  methods: {
    fetchRecept() {
      let receptId = accountStore.state.receptId;
      if (typeof sessionStorage !== 'undefined') {
        receptId = receptId || sessionStorage.getItem('receptId');
      }
      console.log('ID recepta:', receptId); // Ispisuje ID recepta u konzoli
      axios.get(`http://127.0.0.1:8000/api/recept/${receptId}`)
        .then(response => {
          this.recept = response.data;
        })
        .catch(error => {
          console.error(error);
        });
    }
  }
};
</script>
