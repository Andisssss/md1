<template>
    <div class="header"  :style="{ backgroundColor: loggedIn ? headerColor :'#45404B',}">
      <img src="@/assets/logos.svg" alt="Logo" class="logo" />
      <div class="user-info" v-if="loggedIn">
       
        
      
        <div class="avatar" :style="{ backgroundColor: avatarColor }">
          {{ user.name[0] }}
        </div>
        <div class="user-details">
          {{ full_name }}
        </div>
        <div class="separator"></div>
        <button class="pill-button" @click="toggleLogin">{{ 'LOGOUT' }}</button>
      </div>
      <button class="pill-button" @click="toggleLogin" v-else>LOGIN</button>
    </div>
  </template>
  
  <script>


  export default {
    props: {
      loggedIn: Boolean,
    },
    data() {
      return {
        user: {
          name: "Andis",
          surname: "Biksāns",
          code: "IT21036",
        },
        avatarColor: this.getRandomColor(),
      headerColor : '#8645E8',
      };
    },
    computed: {
      full_name() {
        return `${this.user.name} ${this.user.surname}`;
      },
    },
    methods: {
        getRandomColor() {
      const letters = "0123456789ABCDEF";
      let color = "#";
      for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
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
  .avatar {
  width: 40px; 
  height: 40px; 
  text-align: center;
  align-items: center;
  background-color: #2c1272; 
  border-radius: 50%; 
}
.logo {
  width: 60px !important;
  height: auto !important;
}
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #8645E8; 
    padding: 5px;
    height: 50px; 
  }
  .app{
    background-color: #34164d;
  }
  .logo {
    height: 40px;
    width: auto;
  }
  
  .user-info {
    display: flex;
    align-items:center;
  }
  
  .user-details {
  text-align: right;
  color: white;
  font-size: 14px;
  margin-right: 10px;
}
  
  button {
    background: none;
    border: none;
    color: White; 
    font-size: 16px;
    cursor: pointer;
  }
  
  button:hover {
    text-decoration: underline;
  }
  .separator {
  width: 1px; 
  height: 40px; 
  background-color: white;
  margin: 0 10px; 
}

.pill-button {
  background-color: #7a2270; 
  color: #34164d; 
  border: none;
  border-radius: 20px; 
  padding: 5px 15px; 
  font-size: 16px;
  cursor: pointer;
  outline: none;
}

.pill-button:hover {
  background-color: #7a2270; 
}
  </style>
  