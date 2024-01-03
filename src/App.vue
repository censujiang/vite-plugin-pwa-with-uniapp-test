<script setup lang="ts">
//#ifdef H5
// import registerPageAnimation from '@/uni_modules/zy-h5-page-animation/js_sdk/index';
import { useRegisterSW } from 'virtual:pwa-register/vue'
//#endif
onLaunch(() => {
  //#ifdef H5
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
