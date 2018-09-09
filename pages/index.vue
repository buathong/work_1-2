<template>
 <div>
  <v-carousel hide-controls>
    <v-carousel-item
      v-for="(item,i) in items"
      :key="i"
      :src="item.src"
    ></v-carousel-item>
  </v-carousel>
  <nuxt-link to="/table1"><center><h1>Manu</h1></center></nuxt-link><br> 
    </div>
</template>
<script>
  export default {
    data () {
      return {
        items: [
          {
            src: '/pic/caffe.jpg'
          }
          
        ]
      }
    }
  }
</script>