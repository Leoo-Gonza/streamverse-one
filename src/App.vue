<template>
  <!-- configuracion de header -->
  <header>
      <router-link to="/">
         <img :src="'img/Streamverse wh.png'" alt="" class="logo">
      </router-link>
  
  </header>
  <main>
      <router-view/>
  </main>
  <footer class="footer">
    <div class="footer-info">
                    <p>¿Preguntas? Llama al <a href="tel: +54 0800 345 1593">0800 345 1593 (HN)</a></p>
                    <ul class="footer-links">
                        <li class="footer-links__item"><a href="#">Preguntas frecuentes</a></li>
                        <li class="footer-links__item"><a href="#">Preguntas frecuentes</a></li>
                        <li class="footer-links__item"><a href="#">Centro de ayuda</a></li>
                        <li class="footer-links__item"><a href="#">Información corporativa</a></li>
                        <li class="footer-links__item"><a href="#">Términos de uso</a></li>
                        <li class="footer-links__item"><a href="#">Privacidad</a></li>     
                    </ul>

                    <select name="languaje" id="languaje">
                        <option value="es">Español</option>
                        <option value="en">English</option>
                    </select>
                </div>
  </footer>

</template>

<style lang="scss">
    *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family:Arial, Helvetica, sans-serif;

      &::selection{
        background: transparent(#42B883, 0,5 );
      }
    }

    body{
      background-color: #0D0D0D;
    }

    a{
      text-decoration: none;
    }
    header{
      display: flex;
      align-items:flex-start;
      padding: 10px 16px;
      background-color: #000000;
      box-shadow: 0px 0px 6px rgba(0,0,0,0.2);
    }

    .logo{
      width: 150px;
      height: 44px;
    }
    .footer {
  padding: 25px 40px 50px;
  background-color: rgba(0, 0, 0, 0.7058823529);
  width: 100%;
}

.footer a:hover {
  text-decoration: underline;
}

.footer-info {
  max-width: 1000px;
  margin: auto;
}

.footer-info p {
  color: gray;
}

.footer-info p a {
  color: inherit;
  text-decoration: none;
}

.footer-links {
  margin: 20px 0;
  display: flex;
  list-style: none;
  flex-wrap: wrap;
}


.footer-links__item {
  width: 250px;
  min-width: 200px;
}

.footer-links__item a {
  color: gray;
  font-size: 13px;
  margin: 10px;
  text-decoration: none;
}

.footer-links__item a:hover {
  text-decoration: underline;
}

.footer-info select {
  background-color: #000;
  border: 1px solid rgba(128, 128, 128, 0.466);
  color: gray;
  outline: none;
  padding: 13px;
}


@media (max-width: 740px) {
  .login-page {
    background: #000;
  }
  .logo {
    width: 180px;
  }
  .signin {
    background: transparent;
    margin: 0;
    width: 100%;
    padding: 70px 40px 90px;
    border-bottom: 1px solid gray;
  }
}

    @media screen and (max-width: 400px){
      header{
      display: flex;
      align-items:flex-start;
      // justify-content: center;
      // margin-left: 300px;
      padding: 10px 16px;
      background-color: #000000;
      box-shadow: 0px 0px 6px rgba(0,0,0,0.2);
    }
    }
</style>
