<template>
  <div>
    <HeaderComponent />
    <router-view/>
    <div class="wrap">
      <ContentComponent />
      <MenuComponent />
    </div>
  </div>
  <FooterComponent/>
</template>

<script>

import HeaderComponent from "./components/HeaderComponent.vue"
import MenuComponent from "./components/ContentComponent.vue"
import ContentComponent from "./components/MenuComponent.vue"
import FooterComponent from "./components/FooterComponent.vue"


export default {
  name: 'App',
  components: { //components를 사용하기 위해 등록
    HeaderComponent,
    MenuComponent,
    ContentComponent,
    FooterComponent,
    

  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.wrap {
  display: flex;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

</style>
