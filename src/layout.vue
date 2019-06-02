<template>
  <section class="layout authenticated">
    <navbar class="app-navbar is-primary" show-menu-in-mobile-mode>
      <template #brand>
        <navbar-brand>
            <img src="@/assets/logo.png"> <small>admin</small>
        </navbar-brand>
      </template>
      <template #end>
        <div class="navbar-item">
          <burger v-model="drawer" />
        </div>
      </template>
    </navbar>

    <div class="columns is-full-height">
      <drawer v-model="drawer" class="is-2">
        <div v-for="(menu, index) in menuList" :key="index" class="menu">
          <p v-if="menu.divisor" class="menu-label">
            {{ menu.divisor.label }}
          </p>
          <ul class="menu-list">
            <li v-for="(item, idx) in menu.items" :key="idx">
              <a :href="item.to">
                <b-icon
                  :pack="item.iconpack"
                  :icon="item.icon"
                  size="is-small"
                  v-if="item.icon"
                />
                {{ item.text }}
              </a>
            </li>
          </ul>
        </div>
      </drawer>

      <div class="column is-full-height page-content">
        <slot />
      </div>
    </div>
  </section>
</template>

<script>
import Navbar from '@/components/navbar'
import NavbarBrand from '@/components/navbar-brand'
import Drawer from '@/components/drawer'
import Burger from '@/components/burger-icon'

export default {
  components: { Navbar, NavbarBrand, Drawer, Burger },
  data() {
    return {
      userMenu: false,
      drawer: false,
      menuList: [
        {
          items: [
            { text: 'Home', to: '#' },
            { text: 'Link 1', to: '#' },
            { text: 'Link 2', to: '#' },
            { text: 'Link 3', to: '#' }
          ]
        },
        {
          divisor: { label: 'Menu divisor 1' },
          items: [
            { text: 'Link 4', to: '#' },
            { text: 'Link 5', to: '#' }
          ]
        },
        {
          divisor: { label: 'Menu divisor 2' },
          items: [
            { text: 'Link 6', to: '#' }
          ]
        }
      ]
    }
  }
}
</script>

<style lang="scss">
  
  .authenticated {
    .app-navbar {
      .navbar {
        &-end {
          .buttons {
            justify-content: center;
            @media screen and (min-width: 1088px) {
              justify-content: flex-start;
            }
            .button {
              background-color: transparent;
              color: #fff;
              &:hover {
                background-color: rgba(0,0,0, .1)
              }
            }
          }
        }
      }
    }
    .user-menu {
      .dropdown-trigger {
        > a.navbar-item {
          &:hover {
            background-color: rgba(0,0,0, .1)
          }
          .icon {
            margin-left: 10px;
            color: #fff;
            &.is-small {
              height: .8rem;
              width: .8rem;
              font-size:.7rem;
            }
          }
        }
      }
    }
    .drawer {
      &-inner {
        padding: 20px 0;
        .menu {
          .menu-label {
            filter: brightness(150%);
            text-transform: initial;
            padding-left: 25px;
          }
          li {
            a {
              font-size: 0.85rem;
              border-radius: 0;
              padding: 0.5em 1.5em;
              margin: 1em 0;
              border-left: 3px solid transparent;
              &:hover {
                color: #000;
              }
              &.is-active {
                background-color: transparent;
                color: #000;
                .icon {
                }
              }
            }
            .icon {
              margin-right: 20px;
            }
          }
        }
        .menu+.menu {
          margin-top: 15px;
        }
      }
    }
    .page-content {
      overflow: auto;
      background-color: #efefef;

      &.is-full-height {
        min-height: calc(100% + .75rem);
      }
    }
  }
</style>
