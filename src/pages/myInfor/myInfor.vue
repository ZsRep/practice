<template>
<view style="height:100%">
    <view class="infor-fund" style="height:30%;position: relative;">
        <image src="../../static/img/inforBg.png" style="height:100%"></image>
        <view class="myInfor">
            <view class="headImage" style="border-radius: 50%;">
                <image src="../../static/img/test.png"></image>
            </view>
            <view class="infor">
                <view style="margin-bottom: 15px;">{{myRole}}</view>
                <view>￥{{myFund}}</view> 
            </view>
        </view>
        <view class="rechargeCash">
            <view style="width: 100%;border-right: 1px solid white;">
                <button class="infor-bt" @click="goToWithdrawDeposit"><image src="../../static/img/icon.png"></image>提现</button>
            </view>
            <view style="width: 100%;border-left: 1px solid white;">
                <button class="infor-bt" @click="goToRecharge"><image src="../../static/img/icon.png" ></image>充值</button>
            </view>
        </view>
    </view>
    <view style="height:20%;position: relative;box-shadow: 0 2px 3px #FAFAFA;">
        <view class="allOrder">
            <text>全部订单</text>
            <image src="../../static/img/inforNext.png"></image>
        </view>
        <view class="orderState">
            <view class="state">
                <image class="state-icon" src="../../static/img/wait.png"></image><br>
                <text>待接单</text>
            </view>
            <view class="state">
                <image class="state-icon" src="../../static/img/proceeding.png"></image><br>
                <text>进行中</text>
            </view>
            <view class="state" style="margin-right:0">
                <image class="state-icon" src="../../static/img/finish.png"></image><br>
                <text>已完成</text>
            </view>
        </view>
    </view>
    <view class="service" style="height:15%;position: relative;font-size:14px">
        <view class="serviceType">
            <image src="../../static/img/wallet.png"></image>
            <text style="margin-left: 10px;">我的钱包</text>
            <image class="serviceNext" src="../../static/img/inforNext.png">
        </view>
        <view class="serviceType">
            <image src="../../static/img/customService.png"></image>
            <text style="margin-left: 10px;">联系客服</text>
            <image class="serviceNext" src="../../static/img/inforNext.png">
        </view>
    </view>
</view>
</template>

<script>
    export default{
        data(){
            return{
                myRole:'会飞的大象',
                myFund:'600.00'
            }
        },
       methods:{
            goToRecharge(){
                uni.navigateTo({
                    url:'../index/recharge'
                })
            },
            goToWithdrawDeposit(){
                uni.navigateTo({
                    url:'./withdrawDeposit'
                })
            }
       }
    }
</script>

<style>
page{
    width:100%;
    height: 100%;
}
.myInfor{
    display: flex;
    flex-direction: row;
    width: 100%;
    position: absolute;
    bottom: 45%;
}
.headImage image{
    width: 60px;
    height: 60px;
    margin-left: 20px;
}
.infor{
    margin-left: 15px;
    color: white;
    font-size: 16px;
}
.rechargeCash{
    position: absolute;
    bottom: 10%;
    display: flex;
    flex-direction: row;
    width: 100%;
}
.infor-bt{
    background-color: inherit;
    border: 1px solid white;
    height: 30px;
    line-height: 1.9;
    width: 60%;
    color: white;
    font-size:15px;
}
.infor-bt image{
    width: 15px;
    height: 15px;
}
.allOrder{
    color: #323232;
    font-size: 13px;
    width: 95%;
    position: absolute;
    border-bottom: 1px solid #EDEDED;
    left: 5%;
    height: 30%;
    display: flex;
    align-items: center;
}
.allOrder image{
    width: 16px;
    height: 16px;
    position: relative;
    left: 75%;

}
.orderState{
    font-size: 13px;
    color: #323232;
    position: relative;
    top: 40%;
    display: flex;
    justify-content: center;
}
.state{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-right: 19%;
}
.state-icon{
    width: 20px;
    height: 20px;
}
.service image{
    width:17px;
    height:16px
}
.serviceNext{
    width: 16px;
    height: 16px;
    position: relative;
    left: 63%;
}
.serviceType{
    display: flex;
    align-items: center;
    margin-left: 5%;
    margin-top: 10px;
}
</style>