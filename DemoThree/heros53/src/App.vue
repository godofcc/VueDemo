<template>
    <div id="app">
        <app-nav></app-nav>
        <div class="container-fluid">
            <div class="row">
                <div class="col-sm-3 col-md-2 sidebar">
                    <app-slider></app-slider>
                </div>
                <div class="col-sm-9 col-sm-offset-3 col-md-10 col-md-offset-2 main">
                    <router-view></router-view>
                </div>
            </div>
        </div>
    </div>
  
</template>
<script>
    // Animate.css的是使用
    import appNav from './components/common/appnav.vue'
    import appSlider from './components/common/appslider.vue'
    import list from './components/common/list.vue'

    export default {
        name:'app',
        //注册主键
        components:{
            appNav,appSlider,list
        },
        data(){
            return{

            }
        }
    }






</script>
