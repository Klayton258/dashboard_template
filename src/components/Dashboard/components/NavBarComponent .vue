<template>
  <div class="nav-content">
     <div class="title"><i class="fa-brands fa-html5"></i>  LOGO</div>
     <a href="#" @click.prevent="logout" class="logout"><i class="fa fa-sign-out-alt"></i>logout</a>
  </div>
</template>

<script>
export default {
name: 'NavBarComponent',

methods:{
logout(){
  this.$router.push({name:'login'})
}
}

}
</script>

<style lang="scss" scoped>
.nav-content{
  width: 100%;
  display: flex;
  justify-content: space-between;
  padding: 10px 30px;

  .title{
    color: white;
    font-size: 24px;
  }
  .logout{
    color: white;
    font-size: 20px;
  }
  a{
    text-decoration-line: none;
  }
}
</style>