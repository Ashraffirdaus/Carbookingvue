<template>
  <div class="home">
  <app-toolbar></app-toolbar>
  <h1>This is login page</h1>
  
  <template>
  
</template>
    <app-footer></app-footer>
  </div>
</template>

<script>
// Step 1 : Import AppFooter and AppToolbar
import AppFooter from './AppFooter.vue';
import AppToolbar from './AppToolbar.vue';
export default {
  name: 'AppLogin',
  components: {AppFooter , AppToolbar}
  // 2) declare appfooger and apptoolbar
  
}
</script>