<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        child
      </h1>
      <div class="links">
        <!-- <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a> -->
        <button class="button--green" @click="onClick(true)">
          OK
        </button>
        <button class="button--grey" @click="onClick(false)">
          Cancel
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    onClick (opt) {
      const ret = {
        status: opt ? 'success' : 'failed',
        token: opt ? 'hogehoge' : ''
      }
      window.location.href = `http://localhost:3001/callback${this.toQueryString(ret)}`
    },
    toQueryString (obj = {}) {
      const keys = Object.keys(obj)
      let ret = ''
      for (const i in keys) {
        const key = keys[i]
        const value = typeof obj[key] === 'object' ? JSON.stringify(obj[key]) : obj[key]
        ret += +i ? '&' : '?'
        ret += `${key}=${value}`
      }
      return ret
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
