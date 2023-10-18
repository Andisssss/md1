<template>
    <div>
      <h1>ABOUT ME</h1>
      <h3>Name: {{ user.name }}</h3>
      <h3>Surname: {{ user.surname }}</h3>
      <h3>Student code: {{ user.code }}</h3>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        user: {
          name: "Andis",
          surname: "Biksāns",
          code: "IT21036",
        },
      };
    },
  };
  </script>
  <style scoped>
h1,h3{
  color:white;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif ; 
}
</style>
  