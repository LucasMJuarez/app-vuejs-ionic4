<template>
<ion-app>
  <ion-toolbar color="dark">
    <ion-buttons slot="secondary">
      <ion-button @click="goToAbout">
            <ion-icon slot="icon-only" name="logo-ionic"></ion-icon>
      </ion-button>
    </ion-buttons>
    <ion-title @click="goToTitle">
      Ionic Vue
    </ion-title>
  </ion-toolbar>

    <ion-content color="dark">
    <router-view/>

    </ion-content>
</ion-app>

</template>
<script>
export default {
  methods: {
    goToTitle() {
      this.$router.push('/')
    },
    goToAbout() {
      this.$router.push('about')
    }
  }
}
</script>
