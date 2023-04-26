<!-- pagina de inicio -->
<template>
  <div class="login-page">
           <div class="header">
                   <div class="hero">
                       <div class="signin">
                               <h2>Iniciar sesión</h2>
                               <form >
                                   <input type="text" name="name" id="name" placeholder="Email o número de teléfono" autocomplete="off">
                                   <input type="password" name="password" id="password" placeholder="Contraseña">
                                   <router-link to="/home">
                                   <input type="submit" value="Iniciar Sesión">
                                   </router-link>
                                  
                               </form>
                               <div class="help">
                                   <div class="check">
                                       <input type="checkbox" name="remember" id="remember">
                                       <label for="remember">Recuerdame</label>
                                   </div>
                                   <div class="need">
                                       <a href="#">¿Necesitas Ayuda?</a>
                                   </div>
                               </div>
                               <div class="footer-signin">
                                       <a href="#" class="login">
                                           <img :src="'/icon/facebook.svg'" alt="Icon" class="facebook">Inicia sesión con Facebook</a>
                                           <p class="new">¿Nuevo en Streamverse?<a href="#">Registrate ahora</a>
                                           </p>
                                           <p class="protect">Esta página está protegida por Google reCAPTCHA para comprobar que no eres un robot. 
                                               <a href="#">Leer más</a>
                                           </p>
                               </div>
                       </div>
                   </div>
               </div>

       </div>
</template>



<script>

</script>


<style >


.login-page {
 background-image: linear-gradient(to right bottom, rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.445)), url('/public/img/background.jpg');
 background-position: top;
 min-width: 100%;
 min-height: 100%;
}

.header{
   display: flex;
   justify-content: center;
}


.signin {
 background-color: rgba(0, 0, 0, 0.7058823529);
 border-radius: 5px;
 color: #fff;
 margin: 40px auto 100px;
 padding: 70px 60px 150px;
 width: 450px;
}

.signin h2 {
 margin: 0 0 25px;
 font-size: 30px;
}

.signin input {
 display: block;
 color: #fff;
 width: 100%;
 height: 50px;
 border-radius: 5px;
 border: none;
}

.signin input[type=text],
.signin input[type=password] {
 background-color: #353535;
 font-size: 15px;
 outline: none;
 margin-bottom: 20px;
 padding: 0 20px;
}

.signin input[type=text]::-webkit-input-placeholder,
.signin input[type=password]::-webkit-input-placeholder {
 color: #949494;
 font-size: 16px;
}

.signin input[type=submit] {
 background-color: #011640;
 font-size: 16px;
 margin-top: 40px;
 cursor: pointer;
}

.signin .help {
 color: #949494;
 margin-top: 12px;
 padding: 0;
 font-size: 13px;
 display: flex;
 justify-content: space-between;
}

.signin .help .check {
 display: flex;
 align-items: center;
}

.check input {
 width: 20px;
 height: 20px;
}

.check label {
 margin-left: 5px;
 width: 100%;
}

.help .need a {
 text-decoration: none;
 color: #949494;
}

.help .need a:hover {
 text-decoration: underline;
}

.footer-signin {
 margin-top: 30px;
}

.footer-signin .login {
 text-decoration: none;
 color: #727272;
 font-size: 13px;
}

.login .facebook {
 width: 20px;
 vertical-align: middle;
 margin-right: 10px;
}

.footer-signin .new {
 margin-top: 12px;
 font-size: 17px;
 color: #727272;
 font-weight: lighter;
}

.footer-signin .new a {
 color: #fff;
 text-decoration: none;
 margin-left: 5px;
}

.footer-signin .new a:hover {
 text-decoration: underline;
}

.footer-signin .protect {
 margin-top: 12px;
 font-size: 13px;
 color: #9b9b9b;
}

.footer-signin .protect a {
 text-decoration: none;
 color: #5656ff;
}



</style>

