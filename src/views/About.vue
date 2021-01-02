<template>
  <div class="about">
    <router-link to="/" class="back">Back</router-link>
    <div class="card">
      <div class="card-header">
        <img src="../assets/avatar.svg" alt="">
      </div>
      <div class="card-info">
        <h2>Aniruddha Gandhare</h2>
        <p>Web Developer</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {

}
</script>
<style scoped>
  .about{
    position: relative;
    height: 100vh;
    width: 80%;
    margin: 0  auto;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .back{
    position: absolute;
    top: 30px !important;
  }
  .card{
    padding: 20px;
    background-color: white;
    box-shadow: 0px 10px 20px 5px rgba(0,0,0,0.05);
  }
  .card-header{
    flex: 1;
  } 
  .card-info h2{
    font-size: 20px;
    margin-top: 20px;
    text-align: center;  
    color: rgb(0, 255, 0);
  }
  .card-info p{
    text-align: center;
    margin: 6px 0 0 0;

  }

</style>