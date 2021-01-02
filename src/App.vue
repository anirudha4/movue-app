<template>
  
  <router-view/>
</template>

<script>
import { onMounted } from 'vue'
export default {
  setup() {
    onMounted(() => {
      localStorage.setItem('movies', [])
    })
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Rationale&display=swap');

@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@300;400;600;700;800&display=swap');
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Rationale', sans-serif;
}
:root{
  --primary-color: #00ff2a;
}
body{
    background-color: #fff;
}
.container-main{
  height: 300px;
  width: 100%;
  position: relative;
  background-color: #f1f1f1;
  color: white;
  border-bottom: 2px solid rgba(173, 173, 173,0.2);
}

#nav{
  display:flex;
  justify-content: space-between;
  align-items: center;
  padding: 30px 0;
  z-index: 1;
  width: 80%;
  margin: 0 auto;
}
.logo{
  z-index: 1;
  font-size: 40px;
  text-decoration: none;
  color: var(--primary-color);
  position: relative;
}
.nav-link{
  font-size: 18px;
  letter-spacing: 2px;
  text-decoration: none;
  font-weight: bold;
  color:var(--primary-color)
}
.logo:after{
  content: '';
  position: absolute;
  bottom: -5px;
  border-radius: 50px;
  left: 50%;
  transform: translateX(-50%);
  height: 5px;
  width: 50px;
  background-color: rgb(106, 255, 106);
}
form{
    margin-top: 30px;
    position:absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    width: 600px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
.search-bar{
  width: 100%;
  position: relative;
  display: flex;
  transition: all .3s;
  align-items: center;
  margin-bottom: 20px;
}
.search-bar input{
  width: 100%;
  padding: 15px;
  padding-right: 50px;
  outline: none;
  border: none;
  border-bottom: 2px solid transparent;
  border-radius: 3px;
  box-shadow: 0 0 10px 8px rgba(0,0,0,0.02);
  transition: all .3s;
  font-size: 18px;
  letter-spacing: 2px;
  font-weight: bold;
  color: #444;
}
.search-bar input:focus{
  border-bottom: 2px solid var(--primary-color);
  padding-right: 15px;
}
::placeholder{
  letter-spacing: 1px;
  font-weight: bold;
  color: rgb(161, 161, 161);
}
.search-bar img{
  position: absolute;
  display: flex;
  width: 22px;
  right: 15px;
}
input:focus + img{
  display: none;
}
button[type="submit"]{
  padding: 10px 20px;
  border: 2px solid #09ff00;
  cursor: pointer;
  outline: none;
  background: #d7ffde;
  color: var(--primary-color);
  font-weight: bold;
  border-radius: 4px;
  letter-spacing: 2px;
}
.error{
  width: 80%;
  margin: 20px auto;
  padding: 20px;
  background: rgb(255, 233, 233);
  color: red;
  font-weight: bold;
  border-radius: 5px;
}
@media (max-width: 650px){
  form{
    width: 300px;
  }
}
</style>
