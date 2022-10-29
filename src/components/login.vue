<template>
    <div class="login_container">
        <div class="login_box">
            <!-- 头像区域 -->
            <div class="avatar_box">
                <img src="../assets/logo.png" alt="">
            </div>
            <!-- 登录表单区域 -->
            <el-form ref="loginFormRef" :model="loginFrom" :rules="loginFromRules" class="login_form">
                <!-- 用户名 -->
                <el-form-item  prop="username">
                    <el-input v-model="loginFrom.username" prefix-icon="el-icon-user">
                    </el-input>
                </el-form-item>
                <!-- 密码区域 -->
                <el-form-item prop="password" >
                    <el-input type="password" v-model="loginFrom.password" prefix-icon="el-icon-lock">
                    </el-input>
                </el-form-item>
                <!-- 按钮区域 -->
                <el-form-item class="btns">
                    <el-button type="primary" round @click="login">登录</el-button>
                    <el-button @click="resetLogiForm" type="info" round>重置</el-button>
                </el-form-item>
            </el-form>
        </div>
    </div>
</template>
<script>
export default{
    data(){
        return{
            // 登录组件数据绑定
            loginFrom:{
                username:'',
                password:''
            },
            //这是表单的验证对象
            loginFromRules:{
                username:[
                { required: true, message: '请输入登录名称', trigger: 'blur' },
                { min: 4, max: 12, message: '用户名长度在6到12之间', trigger: 'blur' }
                ],
                password:[
                { required: true, message: '请输入密码', trigger: 'blur' },
                { min: 6, max: 18, message: '密码长度在6到18之间', trigger: 'blur' }
                ]
            }
        }
    },
    methods:{
        //重置表单
        resetLogiForm(){
            //console.log(this);
            this.$refs['loginFormRef'].resetFields();               
        },
        login(){
            this.$refs['loginFormRef'].validate(valid => {
                console.log(valid);
            })
        }
    }
};
</script>


<style lang="less" scoped>
    .login_container {
        background:"assets/bg.jpg";
        background-color: #2b4b6b;
        background-size: 100%,100%;
        height: 100%;
    }

    .login_box {
        width: 450px;
        height: 300px;
        background-color: #fff;
        border-radius: 3px;
        position: absolute;
        top: 25%;
        left: 50%;
        transform: translate(-50%, 50%);
    }

    .avatar_box {
        width: 130px;
        height: 130px;
        border: 1px solid #eee;
        border-radius: 50%;
        padding: 10px;
        position: absolute;
        left: 50%;
        transform: translate(-50%, -50%);
        background-color: #fff;
    }

    .avatar_box img{
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background-color: #eee;
        }
        
    .logo_box {
        width: 130px;
        height: 130px;
        border-radius: 50%;
    }
.btns{
    display: flex;
    justify-content: flex-end;
}
.login_form{
    position: absolute;
    bottom: 0;
    width: 100%;
    padding: 0 20px;
    box-sizing: border-box;
}
</style>