<template>
  <div id="select">

    <div v-for="item in items" :key="item.id">
<!--      {{ item.imageUrl  }}-->
      <img
      :src="`https://test-front.framework.team/${item.imageUrl}`"
      height="200px"
      />
      <p>{{ item.name }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'SelectWithOptions',
  // el: '#select',
  data() {
    return {
      items: null
    };
  },
  mounted() {
    axios
        .get('https://test-front.framework.team/paintings')
        .then(response => (this.items = response.data))
        .catch(error => console.log(error));
  }
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
