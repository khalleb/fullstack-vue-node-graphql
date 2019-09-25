<template>
  <div>
    <div id="slogan" class="text-center">
      <h1>GatorName</h1>
      <br>
      <h6 class="text-secondary">Gerador de nomes utilizando Vue.js, Node e GraphQL</h6>
    </div>
    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <h5>Prefixos <span class="badge badge-info">{{ prefixos.length }}</span></h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="prefixo in prefixos" v-bind:key="prefixo">
                    {{ prefixo }}
                  </li>
                </ul>
                <br/>
                <input class="form-control" type="text" placeholder="Digite o prefixo"/>
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>Sufixos <span class="badge badge-info">{{ sufixos.length }}</span></h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                   <li class="list-group-item" v-for="sufixo in sufixos" v-bind:key="sufixo">
                     {{ sufixo }}
                  </li>
                </ul>
                <br/>
                <input class="form-control" type="text" placeholder="Digite o sufixo"/>
              </div>
            </div>
          </div>
        </div>
        <br/>
         <h5>Domínios <span class="badge badge-info">{{ dominios.length }}</span></h5>
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li class="list-group-item" v-for="dominio in dominios" v-bind:key="dominio">
                {{ dominio }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css"
import "font-awesome/css/font-awesome.css"

export default {
  name: 'app',
  data: function(){
    return{
      prefixos:["Maria","João","Ronaldo"],
      sufixos:["Silva","Ribeiro","Barros"],
      dominios:["MariaSilva","MariaRibeiro","MariaBarros","JoãoSilva","JoãoRibeiro","JoãoBarros","RonaldoSilva","RonaldoRibeiro","RonaldoBarros"]
    };
  }
}
</script>

<style>
#slogan {
  margin-top: 30px;
  margin-bottom: 30px;
}
#main {
  background-color: #F1F1F1;
  padding-top: 30px;
  padding-bottom: 30px;

}

</style>
