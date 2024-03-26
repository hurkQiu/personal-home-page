<template>
  <body>
    <main>
      <div class="container">
        <nav>
          <ul>
            <li
              v-for="(item, index) in navItems"
              :key="index"
              :class="['nav-item', { active: navFlag === index }]"
            >
              <b></b>
              <b></b>
              <div @click="selectItem(index)" :class="{ disabled: loading }">
                <RouterLink :to="item.path">
                  {{ item.name }}
                </RouterLink>
              </div>
            </li>
          </ul>
        </nav>
        <div class="content">
          <RouterView v-if="!loading" />
          <div class="loading" v-if="loading">
            <a-progress type="circle" :percent="progress"></a-progress>
          </div>
        </div>
      </div>
    </main>
  </body>
</template>
<script>
import { RouterLink, RouterView, useRouter } from 'vue-router'
import { ref } from 'vue'
import { Progress } from 'ant-design-vue'
export default {
  components: {
    RouterLink,
    RouterView,
    AProgress: Progress
  },
  data() {
    return {
      navItems: [
        { name: 'Home', path: '/' },
        { name: 'Profile', path: '/profile' },
        { name: 'Schedule', path: '/schedule' },
        { name: 'Setting', path: '/setting' }
      ]
    }
  },
  setup() {
    const navFlag = ref(0)
    const router = useRouter()
    const loading = ref(false)
    const progress = ref(0)
    router.beforeEach(() => {
      loading.value = true
    })
    router.afterEach(() => {
      progress.value = 0
      const interval = setInterval(() => {
        progress.value += 10
        if (progress.value >= 100) {
          clearInterval(interval)
          loading.value = false
        }
      }, 50)
    })
    return { navFlag, loading, progress }
  },
  methods: {
    selectItem(index) {
      this.navFlag = index
    }
  }
}
</script>

<style scoped lang="scss">
body {
  background: linear-gradient(aqua, yellow);
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 100%;
}
main {
  width: 100%;
  height: 100%;
}
.logo {
  display: block;
  margin: 0 auto 2rem;
}
nav {
  background: #4d387e;
  color: white;
  border-top-left-radius: 20px;
  border-bottom-left-radius: 20px;
}
li a {
  display: block;
  width: 100%;
  height: 100%;
}
.disabled {
  pointer-events: none;
  opacity: 0.5;
  cursor: not-allowed;
}
.container {
  width: 90%;
  height: 90%;
  position: relative;
  left: 5%;
  top: 5%;
  display: flex;
  grid-template-columns: 15% 85%;
}
.content {
  width: 100%;
  height: 100%;
  display: flex;
}
.loading {
  display: flex;
  height: 100%;
  width: 100%;
  background-color: rgb(255, 255, 255);
  justify-content: center;
  align-items: center;
}
.nav-item {
  position: relative;
  cursor: pointer;
  display: block;
  margin-left: 30px;
  margin-top: 10px;
  padding: 10px;
  :nth-child(1) {
    top: -15px;
  }
  :nth-child(2) {
    bottom: -15px;
  }
}
.nav-item b {
  width: 100%;
  height: 15px;
  position: absolute;
  background: white;
  display: none;
}
.nav-item.active b {
  display: block;
}
.nav-item.active b:nth-child(1)::before {
  content: '';
  position: absolute;
  top: 0;
  right: 10px;
  width: 100%;
  height: 100%;
  border-bottom-right-radius: 20px;
  background: #4d387e;
}
.nav-item.active b:nth-child(2)::after {
  content: '';
  position: absolute;
  top: 0;
  right: 10px;
  width: 100%;
  height: 100%;
  border-top-right-radius: 20px;
  background: #4d387e;
}
.nav-item.active {
  background-color: rgb(255, 255, 255);
  color: black;
  border-top-left-radius: 20px;
  border-bottom-left-radius: 20px;
}
@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;

    padding: 1rem 0;
  }
}
@media (max-width: 1024px) {
  .nav-item {
    margin-top: 30px;
  }
}
</style>
