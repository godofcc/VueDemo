<template>
    <div>
        <div>
            <div v-show="showUserInfo">
                <div class="box">
                    <label>输入用户名</label>
                    <input v-model='username' placeholder="username">
                </div>
                <div class="box">
                    <label>输入邮箱</label>
                    <input v-model='userMail' placeholder="email">
                </div>
                <div class="box">
                    <label>输入手机</label>
                    <input v-model='userPhone' placeholder="userPhone">
                </div>
                <div class="box">
                    <button v-on:click=checkUser()>找回密码</button>
                </div>
            </div>
            <div v-show="showRePassword">
                <div class="box">
                    <label>输入新的密码</label>
                    <input v-model='rePassword' pattern="rePassword">
                </div>
                <div class="box">
                    <button v-on: click=changeUserPassword()>修改密码</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    export default{
        data(){
            return{
                userMail:'',
                userPhone:'',
                username:'',
                rePassword:'',
                showRePassword:false,
                showUserInfo:true,
            }
        },
        methods:{
            checkUser:function(event){
                this.$http.post("http://localhost:3000/users/findPassword",{username:this.username,userMail:this.userMail,userPhone:this.userPhone}).then((data) => {
                    if(data.body.status == 1){
                        alert(data.body.message)
                    }else{
                        alert(data.body.message)
                        this.showRePassword = true
                        this.showUserInfo  = true
                    }
                })
            },
            changeUserPassword:function(event){
                this.$http.post('http://localhost:3000/users/findPassword',{username:this.username,userMail:this.userMail,
                    userPhone:this.userPhone,rePassword:this.rePassword}).then((data) => {
                        if(data.body.status ==1){
                            alert(data.body.message)
                        }else{
                            alert(data.body.message)
                            this.$router.go(-1)
                        }
                    })
            }
        }
    }



</script>
<style>
    .box{
        display: flex;
        justify-content: center;
        align-items: center;
        padding-top: 10px;
    }
</style>