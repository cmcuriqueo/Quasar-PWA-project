<template>
<div> 
  <q-layout
    ref="layout"
    :view="layoutStore.view"
    :left-breakpoint="layoutStore.leftBreakpoint"
    :right-breakpoint="layoutStore.rightBreakpoint"
    :reveal="layoutStore.reveal"
  >
    <q-toolbar slot="header">
      <q-btn flat @click="$refs.layout.toggleLeft()">
        <q-icon name="menu" />
      </q-btn>
      <q-toolbar-title>
        Quasar Layout
        <span slot="subtitle">Empowering your app</span>
      </q-toolbar-title>
      <q-btn class="within-iframe-hide" flat @click="$router.replace('/')" style="margin-right: 15px">
        <q-icon name="keyboard_arrow_left" />
        Go back
      </q-btn>
      <q-btn flat @click="$refs.layout.toggleRight()">
        <q-icon name="menu" />
      </q-btn>
    </q-toolbar>

    <q-tabs slot="navigation" v-if="!layoutStore.hideTabs">
      <q-route-tab slot="title" icon="play_circle_outline" to="#" replace label="Play with Layout" />
      <q-route-tab slot="title" icon="view_array" to="#" replace label="Drawer Panels" />
      <q-route-tab slot="title" icon="pin_drop" to="#" replace label="Fixed Positioning" />
      <q-route-tab slot="title" icon="play_for_work" to="#" replace label="Floating Action Button" />
    </q-tabs>

    <q-scroll-area slot="left" style="width: 100%; height: 100%">
      <q-list-header>Left Panel</q-list-header>
      <q-side-link item to="#">
        <q-item-side icon="account circle" />
        <q-item-main label="Play with Layout" sublabel="Learn more about it" />
        <q-item-side right icon="thumb_up" />
      </q-side-link>
      <q-side-link item to="#">
        <q-item-side icon="view_array" />
        <q-item-main label="Drawer Panels" sublabel="Layout left/right sides" />
      </q-side-link>
      <q-side-link item to="#">
        <q-item-side icon="pin_drop" />
        <q-item-main label="Fixed Positioning" sublabel="...on a Layout" />
      </q-side-link>
      <q-side-link item to="#">
        <q-item-side icon="play_for_work" />
        <q-item-main label="Floating Action Button" sublabel="For Page actions" />
      </q-side-link>

      <div v-if="layoutStore.leftScroll" style="padding: 25px 16px 16px;">
        <p class="caption" v-for="n in 50">
          <em>Left Panel has intended scroll</em>
        </p>
      </div>
    </q-scroll-area>

    <q-scroll-area slot="right" style="width: 100%; height: 100%">
      <q-list-header>Right Panel</q-list-header>
      <div v-if="layoutStore.rightScroll" style="padding: 25px 16px 16px;">
        <p class="caption" v-for="n in 50">
          <em>Right Panel has intended scroll</em>
        </p>
      </div>
    </q-scroll-area>
<div>	
  <img src="~assets/quasar-logo-full.svg" alt="Quasar PWA">
  <div class="hello">

	<div  class="row">
	  <div class="col-4 ">Primera columna </div>
	  <div class="col-4 "> Segunda columna </div>
	  <div class="col-4 "> Tercera columna </div>
	</div>

    <router-link to="/hello"><q-btn icon="sentiment very satisfied">To Hello</q-btn></router-link>
    <q-btn icon="camera" @click="openCamera">Camerae</q-btn>
    <img id="imageFile" src="#"/>
  </div>
</div>
    <q-toolbar slot="footer">
      <q-toolbar-title>
        Footer
      </q-toolbar-title>
    </q-toolbar>
  </q-layout>
</div>
</template>

<script>

import {
  QLayout,
  QToolbar,
  QToolbarTitle,
  QSearch,
  QTabs,
  QRouteTab,
  QBtn,
  QIcon,
  QItemSide,
  QItemMain,
  QSideLink,
  QListHeader,
  QScrollArea
} from 'quasar'
import layoutStore from './layout/layout-store'
export default {
  components: {
    QLayout,
    QToolbar,
    QToolbarTitle,
    QSearch,
    QTabs,
    QRouteTab,
    QBtn,
    QIcon,
    QItemSide,
    QItemMain,
    QSideLink,
    QListHeader,
    QScrollArea
  },
  data () {
    return {
      layoutStore
    }
  },
  name: 'home',
  methods: {
    openCamera(selection) {

      navigator.camera.getPicture(onSuccess, onFail, {  
            quality: 50, 
            destinationType: Camera.DestinationType.DATA_URL 
         });  
         
         function onSuccess(imageData) { 
            var image = document.getElementById('myImage'); 
            image.src = "data:image/jpeg;base64," + imageData; 
         }  
         
         function onFail(message) { 
            //alert('Failed because: ' + message); 
         }
       }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus">
@import '~variables'

ul
  list-style-type none
  padding 0

li
  display inline-block
  margin 0 10px
</style>
