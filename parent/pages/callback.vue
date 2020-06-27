<template>
  <div>
    callback
  </div>
</template>

<script>
export default {
  beforeMount () {
    localStorage.setItem('token', this.$route.query.token)
    window.opener.onClose()
    window.close()
  }
}
</script>

<style>

</style>
