<template>
<view class="o-container" style="height:100%">
    <view class="order-infor" style="height: 24%;box-shadow:0 2px 8px rgb(236, 246, 247)">
        <view class="v-order">
            <image src="../../static/img/incon-or.png"></image>
            <text style="color:#323232;font-size:17px;position: relative;top: 10px;left:10px">{{aera}}</text>
        </view>
        <view style="margin-top:25px" class="v-order">
            <text>角色名称：</text>
            <text>{{role}}</text>
        </view>
        <view style="margin-top:20px" class="v-order">
            <text>段位：</text>
            <text>{{strage}}</text>
        </view>
    </view>
    <view class="order-price" style="height: 23%;box-shadow:0 2px 8px rgb(236, 246, 247)">
        <view class="v-price v-order" >
            <text>单价(元)</text>
            <text class="v-text">{{price}}</text>
        </view>
        <view class="v-price v-order">
            <text>盘数</text>
            <text class="v-text">{{num}}</text>
        </view>
        <view class="v-price v-order">
            <text>总计</text>
            <text class="v-text" style="color:#EEB357">{{total}}</text>
        </view>
    </view>
    <view class="order-notice" style="height: 38%;box-shadow:0 2px 8px rgb(236, 246, 247)">
        <view class="v-order">
            <h5 style="color:#346CD5;margin:10px 0 10px 0;font-weight:900">买家须知</h5>
        </view>
        <view class="v-order">
            <text style="font-size:14px;font-family:'宋体'">
                陪练过程中，如果当前这盘游戏失败、并且陪练员没有被评定为svp，可以及时截图，并在订单页面申请退款、上传当时的截图，
                经核查属实，将会退还给您失败盘数的金额。但如果未达到以上条件，本单局不予以退款。
                如有特殊情况，请至“我的”页面联系客服并描述事实经过，我们会酌情解决。
            </text>
        </view>
    </view>
    <view class="order-submit" style="position:relative;height: 10%">
        <view  style="float:left">
            <text class="total">{{total}}</text>
            <button class="bt-order">提交订单</button>
        </view>
    </view>
</view>
</template>

<script>
    export default{
       data(){
           return {
               aera:'艾欧尼亚 ',
               role:'骑着',
               strage:'白银',
               price:'60.00',
               num:'10' ,
               total:'600.00'
           }
       } 
    }
</script>

<style>
page{
	height: 100%;
    padding: 0;
    margin: 0;
	}
/* .order-infor, .order-price{
    height: 25%;
    border:1px solid black;
} */
.order-infor image{
    width: 22px;
    height: 22px;
    position: relative;
    top: 15px;
}
.v-order{
    width: 90%;
    margin-left: 5%;
}
.v-price{
    margin-top:15px
}
/* .order-notice{
    height: 40%;
    border:1px solid black;
}
.order-submit{
    height: 10%;
    border:1px solid black;
} */
.v-text{
    float: right;
}
.bt-order{
    width:40%;
    height: 100%;
    background-color: #5C92F6;
    color: white;
    border-radius: 0;
    position: absolute;
    right: 0;
    display: inline-block;

}
.total{
    color: #EEB357;
    position: absolute;
    top: 25%;
    margin-left: 15px;
}
</style>