<script setup>
import { ref } from 'vue';
const mostrarCarrinho = ref(false)
const carrinho = ref([])
const livros = ref([
        {
          titulo: "Chain of Iron: Volume 2",
          autor: "Cassandra Clare",
          preco: "23.24",
          imagem: "public/chain_of_iron.png",
        },
        {
          titulo: "Chain of Thorns",
          autor: "Cassandra Clare",
          preco: "23.24",
          imagem: "public/chain_of_trones.png",
        },
        {
          titulo: "City of Fallen Angels",
          autor: "Cassandra Clare",
          preco: "13.94",
          imagem: "public/city_of_fallen.png",
        },
        {
          titulo: "Clockwork Princess",
          autor: "Cassandra Clare",
          preco: "16.84",
          imagem: "public/clockwork_princess.png",
        },
        {
          titulo: "Harlem Shuffle",
          autor: "Colson Whitehead",
          preco: "26.92",
          imagem: "public/harlem_shuffle.png",
        },
        {
          titulo: "Two Old Women",
          autor: "Velma Wallis",
          preco: "13.95",
          imagem: "public/two_women.png",
        },
        {
          titulo: "Carrie Soto is Back",
          autor: "Taylor Jenkins Reid",
          preco: "26.04",
          imagem: "public/taylor_jenkins.png",
        },
        {
          titulo: "Book Lovers",
          autor: "Emily Henry",
          preco: "15.81",
          imagem: "public/book_lovers.png",
        },
      ])
</script>

<template>
  <header>
    <div class="inicio">
      <div class="logo">IFooks</div>
      <p>Apreço a<br>leitura</p>
    </div>
      <input type="text" placeholder="Pesquisar livros..." class="barra-pesquisa" />
      <nav>
        <a href="lancamentos">Temos</a>
        <a href="#">Equipe</a>
        <a href="#">Envio</a>
        <a href="#">Devoluções</a>
      </nav>
      <div class="icons">

        <span>❤️</span>
        <span>👤</span>
        <span @click="mostrarCarrinho = !mostrarCarrinho">🛒</span>
      </div>
    </header>

    <div v-if="!mostrarCarrinho">
     
      <section class="destaque">
        <div class="texto">
          <button class="botao-novo">Novo Autor</button>
          <h1>Eric-Emmanuel Schmitt</h1>
          <p>
            Eric-Emmanuel é um dos autores mais lidos na Europa. Seus livros
            foram traduzidos para 45 idiomas e já venderam mais de 70 milhões de
            cópias no mundo. 3 livros dele também estão disponíveis no Brasil.
          </p>
          <button class="botao-verde">Acessar página do autor</button>
        </div>
        <div class="capa">
          <img src="/public/book.png" alt="">
          <p>*Livro a partir de R$54,00</p>
        </div>
      </section>

  
      <section class="beneficios">
        <div class="item1">🚚 Frete grátis para SC</div>
        <div class="item2">⭐ Livros recomendados</div>
        <div class="item3">🏆 Mais vendidos</div>
      </section>
          
           <section class="lancamentos">
        <h2>Lançamentos</h2>
        <div class="grid-livros">
          <div class="livro" v-for="(livro, index) in livros" :key="index">
            <img :src="livro.imagem" :alt="livro.titulo" />
            <h3>{{ livro.titulo }}</h3>
            <p class="autor">{{ livro.autor }}</p>
            <p class="preco">R${{ livro.preco }}</p>
            <button class="botao-verde" @click="adicionarAoCarrinho(livro)">💚 Comprar</button>
          </div>
        </div>
      </section>
    </div>

<!--carrinho-->
<div v-else class="carrinho">
<h2>Carrinho</h2>
<div class="secoes">
  <div class="titulo">Titulo</div>
  <div class="quantidades">Quantidades</div>
  <div class="subtotal">Subtotal</div>
</div>

 <div>


 </div>

 <div class="botoes">
  <a href="destaques">
  <button>Voltar para loja</button>
  </a>
 <div class="cupons">
  <label>
    <input type="text" placeholder="Código do cupom">
    <button>Inserir cupom</button>
  </label>
 </div>
 </div>
</div>

<!--RODAPÉ-->
    <footer>
      <div class="rodape-superior">
        <div class="logo">IFbooks</div>
        <div class="contato">
          <p>📞 +55 47 40045263</p>
          <p>🕓 8h às 23h - Seg a Sex</p>
          <p>📧 contato@ifbooks.com</p>
          <img src="/public/cartoes.png" alt="">
        </div>
      </div>
      <div class="rodape-inferior">
        <p>© Alguns direitos reservados. IFbooks 2025. </p>
      </div>
    </footer>
</template>

<style scoped>
* {
  margin: 0 ;
  padding: 0;
  box-sizing: border-box;
}

body,
html,
.app {
  font-family: Arial, sans-serif;
  background-color: #fff;
  color: #333;
}
.inicio{
    display: flex;
}
.inicio .logo{
    color: #333;
    margin: 6px 0;
    padding: 0 15px 0 0;
}
.inicio p{
    color:   #2d9246;
    border-left: solid 1px #2d9246 ;
   padding: 0 0 0 15px;
}

.barra-pesquisa {
  padding: 8px 12px;
  border: 1px solid #ccc;
  font-size: 14px;
  outline: none;
  width: 200px;
  transition: all 0.3s ease;
}

.barra-pesquisa:focus {
  border-color: #2d9246;
  box-shadow: 0 0 0 2px rgba(45, 146, 70, 0.2);
}

.icons {
  display: flex;
  align-items: center;
  gap: 15px;
}

.icons span {
  margin-left: 5px;
}
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 40px;
  background-color: white;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 10;
}

.logo {
 
  font-size: 26px;
  color: #2d9246;
}

nav a {
  margin: 0 20px;
  text-decoration: none;
  color: #333;
  font-weight: 500;
  font-size: 14px;
}

nav a:hover {
  color: #2d9246;
}
.icons span {
  margin-left: 20px;
  font-size: 22px;
  cursor: pointer;
  transition: transform 0.2s;
}

.icons span:hover {
  transform: scale(1.2);
}
.destaque {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 60px 40px;
  border-bottom: 1px solid #eee;
  background-color: #fafafa;
}

.destaque .texto {
  max-width: 50%;
  margin-right: 20px;
}

.destaque .texto h1 {
  font-size: 36px;
  color: #2d9246;
  margin: 10px 0;
}

.destaque .texto p {
  font-size: 16px;
  line-height: 1.6;
  color: #555;
}

.botao-novo {
  background-color: white;
  border: 1px solid #2d9246;
  color: #2d9246;
  padding: 6px 12px;
  margin-bottom: 15px;
  font-weight: 600;
  border-radius: 4px;
}

.botao-verde {
  background-color: #2d9246;
  color: white;
  padding: 10px 15px;
  border: none;
  cursor: pointer;
  margin-top: 15px;
  font-weight: 600;
  font-size: 14px;
  border-radius: 6px;
  transition: background 0.3s;
}

.botao-verde:hover {
  background-color: #267a3a;
}

.destaque .capa {
  margin-left: 20px;
  text-align: center;
}

.destaque .capa img {
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.destaque .capa p {
  margin-top: 10px;
  font-size: 14px;
  color: #777;
}

/* Benefícios */
.beneficios {
  display: flex;
  justify-content: space-around;
  padding: 30px 20px;
  background-color: #f3fdf5;
  color: #2d9246;
  font-weight: 500;
  font-size: 25px;
  border-bottom: 1px solid #27AE60;
  border-top: 1px solid #27AE60;
}
.beneficios .item1{
    border-right:solid 1px #937DC2;
    padding: 0vw 8vw 0 0;
}
.beneficios .item2{
    border-right:solid 1px #937DC2;
    padding: 0 8vw 0 0;
}
/* Lançamentos */
.lancamentos {
  padding: 40px 30px;
}

.lancamentos h2 {
  font-size: 28px;
  color: #2d9246;
  margin-bottom: 20px;
  text-align: center;
}

.grid-livros {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 30px;
  margin-top: 20px;
}

.livro {
  background: white;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
  padding: 15px;
  text-align: center;
  transition: transform 0.2s ease;
}

.livro:hover {
  transform: translateY(-5px);
}

.livro img {
  max-width: 100%;
  height: auto;
  border-radius: 6px;
}

.livro h3 {
  font-size: 16px;
  margin: 10px 0 5px;
  color: #333;
}

.autor {
  font-size: 14px;
  color: #777;
}

.preco {
  font-weight: bold;
  margin: 5px 0;
}

/* carrinho*/

div.carrinho h2{
  font-size: 30px;
  margin: 12vw 0 3vw 4vw;
  color: #27AE60;
  font-weight: bold;
  }

  .carrinho .secoes{
   display: flex;
   color: #333;
   margin:0  3vw;
   border-bottom: 3px solid #a7f3c7;
   

  }
  .secoes .titulo {
     margin: 1vw 40vw 1vw 3vw;
     font-weight: bold;
     font-size: 18px;
  }
  .secoes .quantidades {
     margin: 1vw 24vw 1vw 3vw;
     font-weight: bold;
     font-size: 18px;
  }
  .secoes .subtotal {
     margin: 1vw 5vw 1vw 3vw;
     font-weight: bold;
     font-size: 18px;
  }
  .botoes button{
   padding: 10px 30px;
   background-color: white;
    border: 1px solid #b5b6b5;
    border-radius: 3px;
    margin: 2vw 0 2vw 4vw;

  }
  .botoes .cupons input{
     padding: 10px 30px;
     background-color: white;
     border-radius: 3px;
     border: 1px solid #626463;
     margin: 2vw 0 2vw 4vw;
  }
  .botoes .cupons button{
    color: white;
     padding: 10px 30px;
   background-color: #27AE60;
    border: 1px solid #6bf1a3;
    border-radius: 3px;
    margin: 2vw 0 2vw 1vw;
  }

/* Rodapé */
footer {
  background-color: #2d9246;
  color: white;
  padding: 40px 30px;
  margin-top: 40px;
}

.rodape-superior {
  display: flex;
  justify-content: space-between;
  align-items: start;
  flex-wrap: wrap;
  gap: 20px;
}

.rodape-superior .logo {
  font-size: 22px;
  color: white;
  font-weight: bold;
}

.rodape-superior p {
  margin: 5px 0;
  font-size: 15px;
}

.rodape-inferior {
  margin-top: 30px;
  text-align: center;
  font-size: 14px;
  opacity: 0.8;
  border-top:solid 1px;
}
.rodape-inferior p {
    margin: 1vw 0 0 0;
}
.rodape-superior img{
    width: 150px;
    margin: 3vw 0 2vw 0 ;
}

</style>
