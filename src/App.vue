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
										<div class="row">
											<div class="col-md">
												{{ prefixo }}	
											</div>
											<div class="col-md text-right">
												<button class="btn btn-danger" v-on:click="deletePrefixo(prefix)"><span class="fa fa-trash"></span></button>
											</div>
										</div>
									</li>
								</ul>
								<br/>
								<div class="input-group">
									<input class="form-control" type="text" v-model="prefix" v-on:keyup.enter="addPrefixo(prefix)" placeholder="Digite o prefixo"/>
									<div class="input-group-append">
										<button class="btn btn-info" v-on:click="addPrefixo(prefix)"><span class="fa fa-plus"></span></button>	
									</div>
								</div>
							</div>
						</div>
					</div>
					<div class="col-md">
						<h5>Sufixos <span class="badge badge-info">{{ sufixos.length }}</span></h5>
						<div class="card">
							<div class="card-body">
								<ul class="list-group">
									<li class="list-group-item" v-for="sufixo in sufixos" v-bind:key="sufixo">
										<div class="row">
											<div class="col-md">
												{{ sufixo }}
											</div>
											<div class="col-md text-right">
												<button class="btn btn-danger"  v-on:click="deleteSufixo(sufix)"><span class="fa fa-trash"></span></button>
											</div>
										</div>
									</li>
								</ul>
								<br/>
								<div class="input-group">
									<input class="form-control" type="text" v-model="sufix" v-on:keyup.enter="addSufixo(sufix)" placeholder="Digite o sufixo"/>
									<div class="input-group-append">
										<button class="btn btn-info" v-on:click="addSufixo(sufix)"><span class="fa fa-plus"></span></button>	
									</div>
								</div>
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
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";

export default {
	name: "app",
	data: function(){
		return{
			prefix: "",
			sufix:"",
			prefixos:["Maria","João","Ronaldo"],
			sufixos:["Silva","Ribeiro","Barros"],
			dominios:["MariaSilva","MariaRibeiro","MariaBarros","JoãoSilva","JoãoRibeiro","JoãoBarros","RonaldoSilva","RonaldoRibeiro","RonaldoBarros"]
		};
	},
	methods:{
		addPrefixo(prefix){
			this.prefixos.push(prefix);
			this.prefix = "";
			this.generate();
		},
		deletePrefixo(prefix){
			this.prefixos.splice(this.prefixos.indexOf(prefix), 1);
			this.generate();
		},
		addSufixo(sufix){
			this.sufixos.push(sufix);
			this.sufix = "";
			this.generate();
		},
		deleteSufixo(sufix){
			this.sufixos.splice(this.sufixos.indexOf(sufix), 1);
			this.generate();
		},
		generate(){
			this.dominios = [];
			for(const prefix of this.prefixos){
				for(const sufix of this.sufixos){
					this.dominios.push(prefix + sufix);
				}
			}
		}
	}
};
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