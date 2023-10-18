<template>
  <div>
    <HeaderComponent :loggedIn="loggedIn" @login="login" @logout="logout" />
    <div class="container">
      <NavigationComponent v-if="loggedIn" activeTab="activeTab" @changeTab="changeTab" />
      <div class="content">
        <HomeComponent v-if="activeTab === 'home'" />
        <AboutMeComponent v-if="activeTab === 'about'" />
      </div>
    </div>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import NavigationComponent from './components/NavigationComponent.vue';
import HomeComponent from './components/HomeComponent.vue';
import AboutMeComponent from './components/AboutMeComponent.vue';

export default {
  components: {
    HeaderComponent,
    NavigationComponent,
    HomeComponent,
    AboutMeComponent,
  },
  data() {
    return {
      loggedIn: false,
      activeTab: 'home',
    };
  },
  methods: {
    login() {
      if (window.confirm('Do you want to log in?')) {
        this.loggedIn = true;
        this.$emit('login');
      }
    },
    logout() {
      if (window.confirm('Do you want to log out?')) {
        this.loggedIn = false;
        this.$emit('logout');
      }
    },
    changeTab(tab) {
      this.activeTab = tab;
    },
  },
};
</script>

<style scoped>


.container {
  display: flex;
  background-color: #191621;
}
.content {
  flex: 1;
  padding: 20px;
}
.h1{
  color:white;
}
</style>
