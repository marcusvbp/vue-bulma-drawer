<template>
  <aside class="drawer column is-narrow-mobile is-full-height" :class="{ 'is-active': value }">
    <div class="drawer-inner">
      <slot />
    </div>
    <div class="overlay" @click.stop="$emit('input', !value)" />
  </aside>
</template>

<script>
export default {
  name: 'Drawer',
  props: {
    value: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
  .drawer {
    display: flex;
    flex-direction: column;
    overflow: hidden;
    z-index: 100;
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    width: 100%;
    visibility: hidden;
    border-right: 1px solid #dfe2e5;
    padding: 0;
    .overlay {
      position: absolute;
      top: 0;
      right: 0;
      left: 0;
      bottom: 0;
      background-color: rgba(0, 0, 0, .3);
      transition: opacity ease .3s, visibility ease 0 .3s;
      z-index: 99;
      opacity: 0;
      visibility: hidden;
    }
    &-inner {
      width: 40%;
      background-color: #fff;
      transition: all ease .5s;
      flex: 1;
      padding: 0.75rem;
      box-shadow: 0 0 10px rgba(0, 0, 0, .3);
      margin-left: calc(-100% - 1.5rem);
      position: relative;
      z-index: 100;
      @media screen and (max-width: 768px) {
        min-width: 70%;
      }
    }
    &.is-active {
      right: 0;
      visibility: visible;
      .overlay {
        visibility: visible;
        opacity: 1;
        transition: opacity 1s;
      }
      .drawer-inner {
        margin-left: 0;
      }
    }
    @media screen and (max-width: 1086px) {
      &.is-active {
        width: auto;
      }
    }
    @media screen and (max-width: 1230px) {
      min-width: 25%;
    }
    
    @media screen and (min-width: 1087px) {
      // width: auto;
      position: static;
      padding-left: 0.75rem;
      visibility: visible;
      margin-top: 0.75rem;
      &-inner {
        width: auto;
        margin-left: 0;
        box-shadow: none;
      }
      .overlay {
        display: none;
      }
    }
  }
</style>
