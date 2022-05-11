<template>
  <div class="main">
    <div class="sidebar">
      <SideBarComponent />
    </div>
    <div class="content-right">
      <div class="navbar">
        <NavBarComponent />
      </div>
      <div class="content">
        <slot name="slot-content"></slot>
      </div>
    </div>
  </div>
</template>

<script>
import SideBarComponent from "./components/SideBarComponent.vue"
import NavBarComponent from "./components/NavBarComponent .vue"

export default {
  name: 'DashBoardComponent',
  
  components:{
  SideBarComponent,
  NavBarComponent
  }
}

</script>


<style lang="scss" src="./style.scss" scoped />

