<template>
  <a
    :class="{ 'is-active': value }"
    role="button"
    class="navbar-burger burger"
    aria-label="menu"
    aria-expanded="false"
    @click="$emit('input', !value)"
  >
    <span aria-hidden="true" />
    <span aria-hidden="true" />
    <span aria-hidden="true" />
  </a>
</template>

<script>
export default {
  name: 'BurguerIcon',
  props: {
    value: {
      type: Boolean,
      default: false
    }
  }
}
</script>
