<template>
  <div class="sidebar">
     <div class="header row">
         <i class="fa fa-user-circle" style="font-size:50px; margin-bottom:40px"></i>
         <div class="username">Name: Unknow User Loged</div>
     </div>
     <div class="menu">
         <ul>
             <li><router-link :to="{name: 'home'}"><i class="icon fa fa-laptop-house"> </i>   Home</router-link></li>
             <li><router-link :to="{name: 'products'}"><i class="icon fa fa-box icon"> </i>   Products</router-link></li>
             <li><router-link :to="{name: 'clients'}"><i class="icon fa fa-users"> </i>  Clients</router-link></li>
             <li><router-link :to="{name: 'reports'}"><i class="icon fa fa-list-alt"> </i>  Reports</router-link></li>
             <li><router-link :to="{name: 'management'}"><i class="icon fa fa-tasks"> </i>  Management</router-link></li>
         </ul>
     </div>
  </div>
</template>

<script>
export default {
name: 'SideBarComponent'

}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Rajdhani:wght@300;400;500;600&display=swap'); //font-family: 'Rajdhani', sans-serif;
.sidebar{
    height: 100vh;
    width: 100%;
    align-content: center;
    font-family: 'Rajdhani', sans-serif;

    .header{
        text-align: center;
        margin-top: 50px;
        justify-items: center;
        width: 100%;
        color: white;
    }
    .menu{
        margin-top: 30px;
        width: 100%;
    }
    ul{
        padding-left: 30px;
        list-style-type: none;
        font-size: 20px;
    }
    li{
        padding: 10px;

        .icon{
            font-size: 30px;
            padding-right: 20px;
        }
    }
    ul a:hover{
        color: rgb(179, 179, 179);
        font-size: 25px;
    }
    a{
        color: white;
        text-decoration-line: none;
    }
}
</style>