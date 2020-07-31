<template>
<view>
    <view style="margin:30px 0 30px 40px">
        <text>充值金额</text>
    </view>
    <view class="recharge-v" >
        <text style="color:#C8C8C8">￥</text>
        <input class ="recharge-input" type="digit" placeholder="请输入充值金额" v-model="recharge" @input="getRecharge"/>
    </view>
    <view class="re-weixin"> 
        <view style="margin-bottom: 20px">
            <text>微信支付</text>
        </view>
        <view>
            <image class="weixin" src="../../static/img/weiixn.png"></image>
            <text style="position: relative;top: -5px;">微信支付</text> 
            <view class="re-button">
                <view class="check" ref="check" v-model="color" :style="{'background':lineColor}" @click="changeColor"></view>
            </view>
        </view>
    </view>
    <view class="re-sure">
        <view style="width:55%;line-height: 3.5;">
            <text style="color:#323232;margin-left:10px">￥</text>
            <text style="color:#EEB357">{{recharge}}</text></view>
        <view style="width:45%"><button class="re-pay">确认支付</button></view>
    </view>
</view>
</template>

<script>
    export default{
        data(){
            return{
               recharge:'',
               lineColor:''
            }
        },
        methods:{
            getRecharge:function(event){
                this.recharge = event.detail.value
            },
            selectState(e){
                this.whichSelected=e.currentTarget.dataset.state
            },
            changeColor(){
                this.lineColor="blue";
            }
        }
    }
</script>

<style>
.recharge-v{
    border-bottom:1px solid #C8C8C8;
    margin-left: 40px;
    margin-right:40px;
    width:70%;
}
.recharge-input{
    display: inline-block;
    overflow:visible;
}
.re-weixin{
    margin-top: 30px;
    margin-left: 40px;
}
.weixin{
    width: 20px;
    height: 20px;
    margin-right: 10px;
}
.re-button{
    border: 1px solid blue;
    border-radius: 50%;
    height: 20px;
    width: 20px;
    position: relative;
    float:right;
    right: 40px;
}
.check{
    border-radius: 50%;
    width:15px;
    height: 15px;
    padding: 0;
    position: absolute;
    top:50%;
    left: 50%;
    margin: -8px 0 0 -8px;
}
.re-sure{
    width: 100%;
    height: 10%;
    display: flex;
    flex-direction: row;
    position: absolute;
    top: 90%;
    box-shadow: 0 -2px 8px rgb(224, 232, 233)
}
.re-pay{
    width: 100%;
    background-color: #5C92F6;
    border-radius: 0;
    height: 100%;
    color: white;
    line-height: 3.5;
}
</style>