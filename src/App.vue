<template>
<div class="container">
  <nav class="navbar navbar-expand navbar-light dg.light">
    <div class="nav navbar-nav">
      <router-link to="/listar" class="nav-link">Listar pacientes</router-link>
      <router-link to="/Crear" class="nav-link">Crear nuevo paciente</router-link>
    </div>
  </nav>
</div>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
