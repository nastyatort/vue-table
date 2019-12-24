<template>
<div class="header__wrapper">
    <div class="content">
<div class="header" id="header">
    <div id="menu">
        <ul>
            <li v-for="(item, index) in nav" :key="index">{{item}}</li>
        </ul>
    </div>
    <div class="account__wrapper">
        <div class="account">
            <div class="account__icon">
                <img v-bind:src="'src/img/' + avatar" /> 
            </div>
            <div class="account__name">
                <p>Ola,</p>
                <p id="user">{{user}}!</p>
            </div>
        </div>
        <div id="logout">
              <img v-bind:src="'src/img/logout.png'" /> 
        </div>
    </div>
</div>
</div>
</div>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
    user: "SalÃo Dany",
    avatar: 'user.png',
    nav: ["home", "Cadastro do salão", "Cadastro de parceiros", "Visualizar NFSe", "Visualizar DAS"]
    }
  },
  methods: {
  }
}
</script>

<style>
.content{
    width: 1200px;
    margin: auto;
}

p{
    margin: 0;
    padding: 0;
}

.header__wrapper{
    background: #0086c4;
}

.header{
    display: flex;
    align-items: center;
    justify-content: space-between;
}

#menu ul{
  display: flex;
  align-items: center;
  justify-content: space-between;  
  list-style: none;
  padding: 0;
  margin: 0;
}

#menu ul li, p{
    color: white;
    font-family: "Open Sans";
    opacity: 0.7;
    font-size: 14px;
    font-weight: 400;
    line-height: 20px;
}

#menu ul li{
    text-transform: uppercase;
    cursor: pointer;
    padding: 25px 15px;
    font-weight: 700;
}

#menu ul li:hover{
    opacity: 1;
}

#menu ul li.active{
    opacity: 1;
    font-weight: 700;
    position: relative;
}

#menu ul li.active:after{
    content: '';
    position: absolute;
    width: 100%;
    height: 3px;
    left: 0;
    bottom: 0;
    background: white;
}

.account__wrapper{
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.account{
    padding-left: 15px;
    padding-right: 15px;
    min-width: 130px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.account__icon{
    width: 36px;
    height: 36px;
    border-radius: 50%;
    border: 1px solid white;
}

#logout{
    width: 20px;
    height: 20px;
    border-radius: 50%;
    cursor: pointer
}

.account__name p{
    font-size: 14px;
    font-style: italic;
    
}

#user{
    opacity: 1;
    text-transform: none;
    font-style: initial;
    font-weight: 700;
}
</style>