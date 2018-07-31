<template>

<main class="main-detail">
    <article class="detail-film">
        <p class="text-title">{{title}}</p>
        <div class="detail-filmSyp">
            <img :src="imgsrc">
            <p class="text-synopsis">{{synopsis}}</p>
        </div>
    <div class="close-overlay">CLOSE</div>
    </article>
</main>

</template>

<script>
export default {
  name: 'Moviedetail',
  props: {
    imgsrc: String,
    title: String,
    synopsis: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.main-detail{
    z-index:900;
    width:100vw;
    height:100vh;
    background-color:rgba(0,0,0,.5);
    position:absolute;
    top:0}

.detail-film{
    margin:50px auto;
    width:50%;
    background-color:#1e2426;
    border-radius:5px;
    box-shadow:5px 10px 10px #394549;
    font-weight:700;} 

.text-title{
    padding:20px 0 0 20px;
    font-size:20px;}

.detail-filmSyp{
    display:flex;
    flex-flow:row wrap;
    justify-content:space-around;
    margin-bottom:20px;
    padding-left:20px;
    padding-right:20px;
    width:90%;}

.text-synopsis{
    margin-left:20px;
    font-weight:400!important;
    text-align:justify;
    width:70%;} 

.close-overlay{
margin:0 auto!important;
height:40px;
width:100%;
background-color:#0a5d5d;
position:relative;
bottom:0;
display:flex;
cursor:pointer;
justify-content:center;
border-bottom-left-radius:5px;
border-bottom-right-radius:5px;
align-items:center;} 

@media all and (max-width:500px){p{font-size:10px;}section article{max-width:150px}.text-synopsis{margin-left:0;font-size:12px;}}
</style>
