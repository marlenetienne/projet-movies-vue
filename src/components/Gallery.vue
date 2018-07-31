<template>
    <section>
      <!-- <Movie v-for="(item, index) in items" v-bind:key="index" v-bind:imgsrc="getImageUrl(item)" v-bind:title="item.name"/> -->
      <Movie v-for="(item, index) in items" v-bind:imgsrc="item.srcImg" v-bind:title="item.name" v-bind:index="index"
  v-bind:key="item.id" v-on:click.native="onClick(item)"/>
    </section>
</template>

<script>
import Vue from 'vue'
import Movie from './Movie.vue'
import Moviedetail from './Moviedetail.vue'

export default {
  name: 'Gallery',
  props: {
    imgsrc: String,
    title: String,
    index: Number
  },
  components: {
    Movie,
    Vue,
    Moviedetail
  },
  data () {
    return {
      items: []
    }
  },
  async created () {
    try {
      let response = await fetch('movies.json');
      this.items = await response.json();
    }
    catch(error) {
      console.error(error)
    }
  },
  methods: {
    // getImageUrl(item) {
    //   return `/imgs/${item.srcImg}`
    // }
    onClick (item) {
      const composantDetail = Vue.extend(Moviedetail)
      const instance = new composantDetail({
        el:'#detail',
        propsData: {
          imgsrc: item.srcImg,
          title: item.name,
          synopsis: item.synopsis
        }
      })
      console.log(instance)
      instance.$mount()
      console.log(instance.$el)
      console.log(this.$refs["#detail"])
      this.$refs["#detail"].append(instance.$el)
    }
  },
  // $vm0._data.items[0].name
  // methods: {
  //   onClick (key) {
  //     var composantDetail = Vue.extend('Moviedetail')
  //     var instance = new composantDetail({
  //       propsData: {
  //         imgsrc: this.items[key].srcImg,
  //         title: this.items[key].name,
  //         synopsis: this.items[key].synopsis
  //       }
  //     })
  //     instance.$mount()
  //     this.$refs.container.appendChild(instance.$el)
  //   }
  // }
}
</script>

<style scoped lang="less">
section {
    overflow:auto;
    padding:0 50px 0 50px;
    display:flex;
    flex-flow:row wrap;
    flex-grow:1;
    justify-content:space-around;
}
</style>
