<template>
  <div id="app">
    <app-header></app-header>
    <div class="container">
      <div class="panel panel-default">
        <router-view v-title="title"></router-view>
      </div>
    </div>
  </div>
</template>

<script>
import $ from 'jquery'
import AppHeader from './components/header'

import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios)

export default {
  name: 'App',
  data:{
    username: 'Authorization',
    password: 'Rdu76ObLEv7h2PvWheejAM9flRB%2FOPhENecgJgNR19IM1zbQoxLt%2BiBpYMeTcEkTk3pHZ%2FLOCwLiLEdxdu0S6VuTqfyuaJdwyQlEnHPLYUfzQGGs%2B6zB44vXOqKFRH%2BPYyTBpNE4hqRFm0kj7R%2FG1fEg3mRKcZXHSy7TwbVEcxw%3D',
    CommitteeNewsType:[],
    CommitteeLegalRuleAbout:[],
  },
  created(){
    axios.get('/data/GetCommitteeNewsType',{username: this.username,password: this.password}).then((response) => {
      this.CommitteeNewsType = response.data.data;
      console.log(this.CommitteeNewsType);
      //console.log(this.CommitteeNewsType[0].type_name);
    })
    axios.get('/data/GetCommitteeLegalRuleAbout',{username: this.username,password: this.password}).then((response) => {
      this.CommitteeLegalRuleAbout = response.data.data;
      console.log(this.CommitteeLegalRuleAbout);
    })
    
    // axios({
    //   method: 'get',
    //   url: '/data/GetCommitteeLegalRuleAbout',
    //   transformResponse: [function (data) {
    //     return console.log(data);
    //   }],
    //   proxy: {
    //     auth: {
    //       username: 'Authorization',
    //       password: 'Rdu76ObLEv7h2PvWheejAM9flRB%2FOPhENecgJgNR19IM1zbQoxLt%2BiBpYMeTcEkTk3pHZ%2FLOCwLiLEdxdu0S6VuTqfyuaJdwyQlEnHPLYUfzQGGs%2B6zB44vXOqKFRH%2BPYyTBpNE4hqRFm0kj7R%2FG1fEg3mRKcZXHSy7TwbVEcxw%3D'
    //     }
    //   },
    // })
  },
  components: {
    AppHeader
  }
}
</script>

<style lang="less">
@import '~bootstrap/less/bootstrap';
@import './assets/css/customized.css';
@import './assets/css/fonts/font-knst-icon.css';
</style>
