# Revisão

<h2> Criação Api </h2>

<p>1- Criar nova Pasta</p>

<p> 2- iniciar o package json para salvar as nossas dependências  </p>
    
    $ npm init

3- Criar um Arquivo Server.js 


4- Instalar dependencias Express e body parser via npm,
(OBS: o $ indica códigos no terminal não deve ser digitado)

    $ npm i express body-parser --save
    $ npm i nodemon --save -dev 
    


5- Delacrar instanciar o Express e executar o body parser

```javascript
const express = require('express')
const bodyParser = require('body-parser')

const app = express()
app.use(bodyParser.json)
```
    
6-  Configurar a porta da Api

```javascript
Const port = 3000
app.listen(port, () => {
console.log(`Api rodando na porta ${port}!`)
})
```
    
    
7- Configurar rota Raiz da Api

```javascript
app.use("/", (req,res) => {})
```
    

8- Criar uma rota para Media

```javascript
app.post("/media", (req, res) => {
let idade1 = parseFloat(req.body.idade1);
let idade2 = parseFloat(req.body.idade2);
let media = (idade1 + idade2) / 2;
res.send("Media " + media)
})
```

<h2> Criação Front-End </h2>
Caso ainda não tenha feito, instale globalmente o vue pelo comando

```
$ npm install -g @vue/cli
```

Em um novo diretório fora da api execute o  $ vue create app

```
$ vue create app
```

Selecione apenas o Babel e o Router, nao usar history mode e as configurações em arquivos separados ou no package json.


Entre na pasta app, ou o qualquer nome que voce tenha dado, e adicione o vuetify
```
$ cd app
$ vue add vuetify
```

Para verificar se o vue foi instalado corretamente abra o servidor pelo comando
```
$ npm run serve
```

Para criamos uma nova tela, crie um novo arquivo Media.vue na pasta Views dentro da pasta src com o formato padrão do Vue, um tag de template e outra de script

```html
<template>
  <div class="home">
    Home 
  </div>
</template>

<script>
export default {
  name: 'home',
  components: {
    
  }
}
</script>
```

Dentro da do arquivo de rotas na pasta ./src/routes/index.js , cadastre  uma nova rota seguindo o modelo 

```javascript
{
    path: '/media',
    name: 'media',
    // route level code-splitting
    // this generates a separate chunk (about.[hash].js) for this route
    // which is lazy-loaded when the route is visited.
    component: () => import(/* webpackChunkName: "about" */ '../views/Media.vue')
  },

```

Para cadastrar o roteador e vizualiar esta nova rotas, precisamos adicionar o gerenciardor de rotas ao app, no arquivo ./src/App.vue , adicione  a tag <router-view> para mostrar as rotas cadastradas

```html
<template>
  <v-app >
    <v-content >
        <v-container fluid>
            <router-view></router-view>
        </v-container>
    </v-content>
  </v-app>
<template>
```

Agora que podemos acessar esta rota, devemos adicionar nela os botões e campos no nosso arquivo ./src/views/Media.vue usando tags do vuetify

```html
<template>
  <v-form>
    <v-container>
        <v-row>
            <v-col> 
                <v-text-field label="idade1"/>
            </v-col>
            <v-col>
                <v-text-field label="idade2"/>
            </v-col>
            <v-col>
                <v-btn>Calc</v-btn>
            </v-col>
        </v-row>
    </v-container>
  </v-form>
</template>
```
