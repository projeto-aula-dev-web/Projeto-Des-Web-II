<script setup>

</script>

<template>
     <!-- Cabeçalho -->
    <header>
      <div class="logo">IFooks</div>
      <input type="text" placeholder="Pesquisar livros..." class="barra-pesquisa" />
      <nav>
        <a href="#">Início</a>
        <a href="lancamentos">Lançamentos</a>
        <a href="#">Mais vendidos</a>
        <a href="#">Contato</a>
      </nav>
      <div class="icons">
        <input type="text" placeholder="Pesquisar livros..." class="barra-pesquisa" />
        <span><i class="fa-solid fa-heart"></i></span>
        <span><i class="fa-solid fa-user"></i></span>
        <span @click="mostrarCarrinho = !mostrarCarrinho"><i class="fa-solid fa-cart-shopping"></i></span>
      </div>
    </header>
</template>

<style scoped>

</style>
