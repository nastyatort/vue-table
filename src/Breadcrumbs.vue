<template>
<div class="content">
<div class="breadcrumbs">
    <ul class="breadcrumbs__list">
        <li class="breadcrumbs__item"><img v-bind:src="'src/img/home.png'" /> </li>
        <li class="breadcrumbs__item">first</li>
        <li class="breadcrumbs__item">second</li>
        <li class="breadcrumbs__item">third</li>
    </ul>
</div>
</div>
</template>

<script>
export default {
    name: 'Breadcrumbs',
    data () {
      return {
       
      }
    },
    methods: {
    }
  }
</script>

<style>
.breadcrumbs__list{
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding: 0
}

.breadcrumbs__list li{
  color: #0c436a;
font-family: "Open Sans";
font-size: 14px;
font-weight: 300;
font-style: italic;
position: relative;
margin-left: 20px;
list-style: none;
}

.breadcrumbs__list li:before{
   position: absolute;
   left: -10px;
   top: 0;
   content: '/'
 }
 
 .breadcrumbs__item:first-child:before{
   display: none
 }

  .breadcrumbs__item{
    cursor: pointer;
  }

</style>