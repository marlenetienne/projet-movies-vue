<template>
<article>
  <figure class="border-image">
    <!-- <img :src="imgsrc" :id="key" v-on:click="onClick(id)"> -->
    <img :src="imgsrc" :index="index" v-on:click="onClick(index)">
  </figure>
  <p>{{title}}</p>
</article>
</template>

<script>
import Moviedetail from './Moviedetail.vue'

export default {
  name: 'Movie',
  props: {
    imgsrc: String,
    title: String,
    index: Number
  },
  components: {
    Moviedetail
  },
  methods: {
    onClick (index) {
      console.log(index)
      const composantDetail = Vue.extend(Moviedetail)
      const instance = new composantDetail({
        propsData: {
          imgsrc: items[index].srcImg,
          title: items[index].name,
          synopsis: items[index].synopsis
        }
      })
      console.log(instance)
      instance.$mount()
      this.$refs.container.appendChild(instance.$el)
    }
  }
}
</script>

<style scoped lang="less">

  p {
    font-size:16px;}

  article{
    max-width:215px;
    max-height:340px;
    margin:20px;
  }  

  .border-image{ 
    overflow:hidden;
    margin:0;
    border-radius:5px;
    box-shadow:5px 10px 10px #394549;
    display:flex;
    border:solid 0 #00f;
    transition:border 1s ease-out; 

    &:hover {
      border:solid 5px #00f;
    }
  }

  section article {
    img{
      -webkit-transition:transform 1s ease-out;
      transition:transform 1s ease-out;
    }   
    img:hover {
      cursor:pointer;
      transform:scale(1.5,1.5);
    }    
    p {
      white-space:nowrap;
      overflow:hidden;
      text-overflow:ellipsis;
    }
  } 
</style>
