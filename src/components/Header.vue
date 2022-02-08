<template>
  <div id="nav">
    <div class="for__img">
      <img
        src="../../public/img/Logo_imi_horizontal.png"
        class="img__logo"
        alt=""
      />
    </div>
    <p class="for__links">
      <router-link to="/">Форма &nbsp;&nbsp;</router-link> |
      <router-link to="/preview"> &nbsp;&nbsp;Превью</router-link>
    </p>
  </div>
</template>

<style>
#nav {
  padding: 15px;
  border-bottom: 0.5px solid rgba(17, 17, 17, 0.1);
  height: 5vh;
}

#nav a {
  font-family: Montserrat;
  font-weight: 400;
  color: #111111;
  text-decoration: none;
  font-size: 18px;
}

#nav a.router-link-exact-active {
  font-weight: 600;
  color: #2c2c2c;
}

#nav .for__img {
  position: absolute;
  display: inline;
  left: 20px; }
#nav .img__logo {
  width: 175px;
}
#nav .for__links{
   display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  margin-bottom: 20px;
}
</style>
