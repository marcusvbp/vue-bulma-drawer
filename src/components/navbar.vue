<template>
  <nav class="navbar" role="navigation" aria-label="main navigation" :class="{ 'show-in-mobile': showMenuInMobileMode }">
    <div class="navbar-brand">
      <span v-if="burgerPosition === 'left' && !showMenuInMobileMode" class="navbar-item">
        <burger v-model="mobileShow" />
      </span>
      <slot name="brand" />
      <burger v-if="burgerPosition === 'right' && !showMenuInMobileMode" v-model="mobileShow" />
    </div>

    <div :class="{ 'is-active': mobileShow }" class="navbar-menu">
      <div class="navbar-start">
        <slot name="menu" />
      </div>

      <div class="navbar-end">
        <slot name="end" />
      </div>
    </div>
  </nav>
</template>

<script>
import Burger from './burger-icon'

export default {
  name: 'Navbar',
  components: { Burger },
  props: {
    burgerPosition: {
      type: String,
      default: 'right',
      validator: v => ['left', 'right'].includes(v)
    },
    showMenuInMobileMode: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      mobileShow: false
    }
  }
}
</script>

<style lang="scss">
  .navbar {
    &.show-in-mobile {
      display: flex;
      .navbar-brand {
        flex: 1;
      }
      .navbar-menu {
        @media screen and (max-width: 1087px) {
          display: block;
          box-shadow: none;
          background-color: transparent;
        }
      }
      .navbar-end {
        @media screen and (max-width: 1087px) {
          display: flex;
          .navbar-item {
            display: flex;
            align-items: center;
          }
        }
      }
    }
  }
</style>
