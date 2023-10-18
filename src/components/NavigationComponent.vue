<template>
    <div class="navigation" >
      <button
        :class="{ active: activeTab === 'home' }"
        @click="changeTab('home')"
      >
        Home
      </button>
      <button
        :class="{ active: activeTab === 'about' }"
        @click="changeTab('about')"
      >
        About me
      </button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      activeTab: String,
      loggedIn: Boolean
    },
    methods: {
      changeTab(tab) {
        this.$emit('changeTab', tab);
      },
      toggleLogin() {
        if (this.loggedIn) {
          this.$emit('logout');
        } else {
          if (window.confirm('Do you want to log in?')) {
            this.$emit('login');
          }
        }
      },
    },
  };
  </script>
  
  <style scoped>
.navigation {
  display: flex;
  flex-direction: column;
  align-items: center; 
  padding: 15px;
  width: 18%;

}

button {
  background: none;
  border: none;
  color: white;
  font-size: 16px;
  cursor: pointer;
  margin: 5px 0; 
}

button.active {
  font-weight: bold;
  color: #8645E8;
  background: #8645E8 !important; 
}
</style>