<script setup lang="ts">
onLaunch(async () => {
  //#ifdef H5
  const { useRegisterSW } = await import('virtual:pwa-register/vue')
  useRegisterSW({
    immediate: true,
  })
  try {
    if ('serviceWorker' in navigator) {
      window.addEventListener('load', () => {
        navigator.serviceWorker.register('/sw.js', { scope: './' })
      })
    }
  } catch { }
  //#endif
})
</script>
