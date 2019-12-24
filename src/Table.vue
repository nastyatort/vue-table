<template>
<div class="content">
<div class="filter__wrapper">
    <div class="filter__item">
        <h6>Periodo</h6>
                <div class="date__wrapper">
        <div class="date">
            <input>
        </div>
        <div><p>a</p></div>
        <div class="date">
            <input>
        </div>
    </div>
    </div>

    <div class="filter__item">
        <h6>tipo de serviço</h6>
        <input v-model="type" type="text">
        <div v-on:click="selectCategory = 'type'" class="search">
            <img v-bind:src="'src/img/search.png'" /> 
        </div>
    </div>


    <div class="filter__item">
        <h6>Parceiro selecionado</h6>
        <select v-on:click="selectCategory = 'name'" v-model="name">
            <option value="">Parceiro selecionado</option>
            <option v-for="(item, index) in info" :key="index">{{item.name}}</option>
        </select>
    </div>
</div>

<div class="table__wrapper">
    <div class="table__title">
        <div class="table__icon">
<img v-bind:src="'src/img/' + table" /> 
        </div>
        <h2>NFSe</h2>
    </div>
    
    <div class="table__content">
        <table>
            <thead>
                <tr>
                    <th v-for="(item, index) in title" :key="index">{{item}}</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item) in filter()" :key="item.id">
                    <td>{{item.name}}</td>
                    <td>{{item.cnpj}}</td>
                    <td>{{item.dateFrom}}</td>
                    <td>{{item.dateTo}}</td>
                    <td>{{item.coast}}</td>
                    <td>{{item.type}}</td>
                    <td v-on:click="action(item.id)" class="action"><img v-bind:src="'src/img/show.png'" /> </td>
                </tr>
            </tbody>
        </table>
    </div>
</div>

<div class="button__wrapper">
    <button v-on:click="clearFilter()" id="fetchar">Clear filter</button>
    <button v-on:click="report()" id="gerar">gerar relatório</button>
</div>

</div>
</template>

<script>
export default {
    name: 'Table',
      data () {
    return {
        type: '',
        name: '',
        selectCategory: 'all',
        table: 'table.png',
        title: ["Parceiro", "CNPJ", "Período De", "Período Até", "Valor R$", "Tipo De Serviço", "Açao"],
        info: [
            {id: '1id', name: "Jozé da Silva Sauro", cnpj: "00.89.89/0001-09", dateFrom: "25/11/2019", dateTo: "25/11/2019", coast: "100,00", type: "Cabeleireiro aa"},
            {id: '2id', name: "Neideleine Rocha Nide", cnpj: "00.89.89/0001-09", dateFrom: "23/11/2019", dateTo: "23/11/2019", coast: "189,00", type: "Barbeiro"},
            {id: '3id', name: "Jozé da Silva Sauro", cnpj: "00.89.89/0001-09", dateFrom: "25/11/2019", dateTo: "25/11/2019", coast: "100,00", type: "Cabeleireiro"},
            {id: '4id', name: "Neideleine Rocha Nide", cnpj: "00.89.89/0001-09", dateFrom: "23/11/2019", dateTo: "23/11/2019", coast: "189,00", type: "Barbeiro"},
            {id: '5id', name: "Jozé da Silva Sauro", cnpj: "00.89.89/0001-09", dateFrom: "25/11/2019", dateTo: "25/11/2019", coast: "100,00", type: "Cabeleireiro"},
            {id: '6id', name: "Neideleine Rocha Nide 123", cnpj: "00.89.89/0001-09", dateFrom: "23/11/2019", dateTo: "23/11/2019", coast: "189,00", type: "Barbeiro"}
            ]
    }
  },
  methods: {
      filter(){
          switch(this.selectCategory){
            case "all":
                this.selectCategory;
            case "name":
                if(this.name !== ''){
                return this.info.filter(el => el.name ===  this.name)
            }else{
                return this.info
            }
            case "type":
              return this.info.filter(el => el.type.toLowerCase().indexOf(this.type.toLowerCase()) !== -1)  
          }
      },
      clearFilter(){
          this.type = ''
          this.name = ''
      },
      report(){
          console.log('show report')
      },
      action(id){
          alert(id)
      }
  }
}
</script>

<style>

.action{
    cursor: pointer;
}

.filter__wrapper{
margin: 30px 0;
    width: 80%;
    display: flex;
    align-items: center;
    justify-content: space-between
}

.filter__wrapper input, .filter__wrapper select, .filter__wrapper p{
    color: #0c436a;
font-family: "Open Sans";
font-size: 16px;
font-weight: 300;
font-style: italic;
outline: none
}
.filter__wrapper input, .filter__wrapper select{
    border: none;
    border-bottom: 1px solid lightgray;
    width: 240px;
}

.filter__wrapper .date input{
    width: 130px;
}

.filter__item{
    position: relative;
}

.search{
    position: absolute;
    right: 0;
    top: 33px;
    width: 16px;
    height: 16px;
    cursor: pointer;
}

h6{
    font-size: 14px;
    margin: 10px 0;
    text-transform: uppercase;
    color: #0c436a;
font-family: "Open Sans";
font-size: 14px;
font-weight: 700;
}

.date__wrapper{
    display: flex;
    align-items: center;
    justify-content: flex-start
}


.filter__wrapper p{
    margin: 0 30px;
}

.table__wrapper .table__title{
    display: flex;
    align-items: center;
    justify-content: flex-start
}

.table__wrapper .table__title .table__icon{
    height: 36px;
    width: 32px;
    margin-right: 15px
}

.table__wrapper .table__title h2{
 color: #000000;
font-family: "Open Sans";
font-size: 24px;
font-weight: 700;
line-height: 16px;
}

.table__wrapper table{
    box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16);
border-radius: 4px;
border-collapse: separate; 
    width: 100%;
    border-spacing: 7px 11px;
    margin-top: 20px;
}

.table__wrapper table tr{
    border-bottom: 1px solid lightgray
}

.table__wrapper table tr th{
    color: #0c436a;
font-family: "Open Sans";
font-size: 16px;
font-weight: 700;
line-height: 24px;
text-align: left
}

.table__wrapper table tr td{
    color: #0c436a;
font-family: "Open Sans";
font-size: 16px;
font-weight: 300;
font-style: italic;
line-height: 24px;
}

.button__wrapper{
    display: flex;
    align-items: center;
    justify-content: flex-end;
    margin-top: 30px
}

.button__wrapper button{
    border-radius: 20px;
    outline: none;
    border: none;
    width: 180px;
    height: 46px;
    color: #0c436a;
font-family: "Open Sans";
font-size: 14px;
font-weight: 700;
text-transform: uppercase;
cursor: pointer;
}

.button__wrapper #fetchar{
background-color: #ffffff;
border: 1px solid #d1d3d4;
margin: 0 30px
}

.button__wrapper #gerar{
    border: 1px solid rgba(255, 255, 255, 0);
background-color: #38f16f;
}

</style>