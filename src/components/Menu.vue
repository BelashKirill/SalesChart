<template>
  <ul class="menu">
    <transition-group name="flip-list">
      <li class="menu__item overview">
        <a href="#" class="menu__link">Overview</a>
      </li>
      <li class="menu__item pages" :class="{ open: category === 'pages' }" @click="toggleMenu('pages')">
        <a href="#" class="menu__link">Pages</a>
        <Transition name="slide-fade">
          <ul class="submemu" v-if="category === 'pages'">
            <li class="submemu__item">
              <a href="#" class="submenu__link">Product List</a>
            </li>
            <li class="submemu__item">
              <a href="#" class="submenu__link">Billing</a>
            </li>
            <li class="submemu__item">
              <a href="#" class="submenu__link">Invoice</a>
            </li>
          </ul>
        </Transition>
      </li>
      <li class="menu__item sales active" :class="{ open: category === 'sales' }" @click="toggleMenu('sales')">
        <a href="#" class="menu__link">Sales</a>
        <Transition name="slide-fade">
          <ul class="submemu" v-if="category === 'sales'">
            <li class="submemu__item">
              <a href="#" class="submenu__link">Product List</a>
            </li>
            <li class="submemu__item">
              <a href="#" class="submenu__link">Billing</a>
            </li>
            <li class="submemu__item">
              <a href="#" class="submenu__link">Invoice</a>
            </li>
          </ul>
        </Transition>
      </li>
      <li class="menu__item messages" :class="{ 'small-txt': messageNumber === '99+' }">
        <a href="#" :num="messageNumber" class="menu__link">Messages</a>
      </li>
      <li class="menu__item auth" :class="{ open: category === 'auth' }" @click="toggleMenu('auth')">
        <a href="#" class="menu__link">Authentication</a>
        <Transition name="slide-fade">
          <ul class="submemu" v-if="category === 'auth'">
            <li class="submemu__item">
              <a href="#" class="submenu__link">Product List</a>
            </li>
            <li class="submemu__item">
              <a href="#" class="submenu__link">Billing</a>
            </li>
            <li class="submemu__item">
              <a href="#" class="submenu__link">Invoice</a>
            </li>
          </ul>
        </Transition>
      </li>
    </transition-group>
  </ul>
  <div class="menu-sep"></div>
  <ul class="menu">
    <li class="menu__item docs">
      <a href="#" class="menu__link">Docs</a>
    </li>
    <li class="menu__item comp">
      <a href="#" class="menu__link">Components</a>
    </li>
    <li class="menu__item help">
      <a href="#" class="menu__link">Help</a>
    </li>
  </ul>
</template>

<script>
export default {
  name: "Menu",
  props: {
    numMess: Number,
  },
  data() {
    return {
      category: "sales",
    };
  },
  methods: {
    toggleMenu(name) {
      if (this.category === name) {
        this.category = "";
      } else {
        this.category = name;
      }
    },
  },
  computed: {
    messageNumber() {
      if (this.numMess > 99) {
        return "99+";
      } else {
        return this.numMess;
      }
    },
  },
};
</script>

<style lang="scss">
.menu {
  padding: 0 12px;

  &__item {
    margin-bottom: 13px;
  }

  &__link {
    display: flex;
    align-items: center;
    padding: 4px 8px;
    border-radius: 12px;
    font-weight: 500;
    color: #111827;
  }

  &__overview-link {
    color: #1c64f2;
  }
}

.overview {
  a {
    color: #1c64f2;

    &::before {
      content: "";
      display: block;
      width: 24px;
      height: 24px;
      margin-right: 15px;
      background: url("@/assets/img/chart-pie.svg");
    }
  }
}

.active {
  a {
    background: #f3f4f6;
  }
}

.pages {
  a {
    &::before {
      content: "";
      display: block;
      width: 24px;
      height: 24px;
      margin-right: 15px;
      background: url("@/assets/img/document-report.svg");
    }

    &::after {
      content: "";
      display: block;
      width: 22px;
      height: 22px;
      margin-left: auto;
      background: url("@/assets/img/chevron-down.svg") no-repeat;
      transition: ease-out 0.4s;
    }
  }
}

.sales {
  @extend .pages;

  a {
    &::before {
      background: url("@/assets/img/shopping-bag.svg");
    }
  }
}

.messages {
  @extend .pages;

  a {
    &::before {
      background: url("@/assets/img/inbox-in.svg");
    }

    &::after {
      content: attr(num);
      display: flex;
      align-items: center;
      justify-content: center;
      width: 20px;
      height: 20px;
      font-size: 12px;
      color: #9b1c1c;
      background: #fbd5d5;
      border-radius: 100%;
    }
  }
}

.auth {
  @extend .pages;

  a {
    &::before {
      background: url("@/assets/img/lock-closed.svg");
    }
  }
}

.docs {
  @extend .pages;

  a {
    &::before {
      background: url("@/assets/img/clipboard-list.svg");
    }

    &::after {
      display: none;
    }
  }
}

.comp {
  @extend .pages;

  a {
    &::before {
      background: url("@/assets/img/collection.svg");
    }

    &::after {
      display: none;
    }
  }
}

.help {
  @extend .pages;

  a {
    &::before {
      background: url("@/assets/img/support.svg");
    }

    &::after {
      display: none;
    }
  }
}

.menu-sep {
  width: 100%;
  height: 1px;
  background: #e5e7eb;
  margin: 20px 0;
}

.small-txt {
  a {
    &::after {
      font-size: 9px;
    }
  }
}

.open {
  a {
    &::after {
      transform: rotate(180deg);
    }
  }
}

.submemu {
  padding-left: 47px;
  &__item {
    margin: 0 0 27px;

    a {
      font-weight: 500;
      color: #111827;
      background: none;

      &::before,
      &::after {
        display: none;
      }
    }

    &:last-child {
      margin-bottom: 28px;
    }

    &:first-child {
      margin-top: 15px;
    }
  }
}

.slide-fade-enter-active {
  transition: all 0.8s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.1s;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(-20px);
}

.flip-list-move {
  transition: transform 0.8s;
}

.flip-list-leave {
  transition: transform 0.8s;
}
</style>
