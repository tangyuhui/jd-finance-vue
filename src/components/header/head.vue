<template>
    <header id='head_top'>
       <div class="left">
          <span>注册</span>
           <span>|</span>
          <span>登录</span>
       </div>
       <div class="center">
           <img class="jr-logo" src="//m.jr.jd.com/spe/qyy/main/images/jr-logo.png" width="105px" height="28px">
       </div>
       <div class="right">
         <button class="btn-dwn">APP下载</button>
       </div>
    </header>
</template>

<script>
    import {mapState, mapActions} from 'vuex'
    export default {
    	data(){
            return{

            }
        },
        mounted(){
            //获取用户信息
            this.getUserInfo();

        },
        props: [],
        computed: {
            ...mapState([
                'userInfo'
            ]),
        },
        methods: {
            ...mapActions([
                'getUserInfo'
            ]),
        },

    }

</script>

<style lang="scss" scoped>
    @import '../../style/mixin';

    #head_top{
        background-color: $fc;
        top:0;
        left:0;
        position:fixed;
        @include wh(100%,50px);
        display:flex;
        justify-content:space-between;
        align-items:center;
        z-index:10;
    }
    .left{
      margin-left:10px;
      font-size:14px;
      color:#666;
    }
    .btn-dwn{
     background-color:#F04752;
     width:60px;
     height:28px;
     line-height:28px;
     color:#fff;
     margin-right:10px;
    }

</style>
