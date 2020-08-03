<template>
<view class="o-container" style="height:100%">
    <view class="order-infor" style="height: 24%;box-shadow:0 2px 8px rgb(236, 246, 247)">
        <view class="v-order">
            <image src="../../static/img/incon-or.png"></image>
            <text style="color:#323232;font-size:17px;position: relative;top: 10px;left:10px">{{aera[index].name}}</text>
        </view>
        <view style="margin-top:25px" class="v-order">
            <text>角色名称：</text>
            <text>{{role}}</text>
        </view>
        <view style="margin-top:20px" class="v-order">
            <text>段位：</text>
            <text>{{arrayStage[Stageindex].name}}</text>
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
            <text class="v-text" style="color:#EEB357">{{num * price}}</text>
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
            <text class="total">{{num * price}}</text>
            <button class="bt-order" @click="openPrompt">提交订单</button>
            <uni-popup ref="popupt" type="center">
				<view class="nui-tip1" style="position:relative;margin:0">
					<view style="background-color:white;opacity:1 ;width: 260px;height: 240px;" class="popup-v">
						<view>
							<image src="../../static/img/prompt2.png" style="width: 260px;height: 90px;position: relative;left: 50%;margin-left: -130px"></image>
					    </view>
					    <view style="color:white;font-size:15px;position: relative;top: -28%;left: 15px;">订单支付</view>
                        <view stye="font-size:14px">
                            <view style="margin-bottom:15px"><text style="margin: 0 70px 0 20px">所需支付：</text>
                            <text>￥</text><text style="color:#EEB357">{{num * price}}</text>
                            </view>
                            <view><text style="margin: 0 70px 0 20px">钱包余额：</text>
                            <text>￥</text><text style="color:#EEB357">{{remain}}</text></view>
				        </view>
                        <view style="position: relative;top: 20px;">
                           <navigator url="/pages/index/recharge" hover-class="navigator-hover">
                                <button class="recharge">去充值</button>
                           </navigator>
                            <button class="replay" @click="confirmPay">确认支付</button>
                        </view>
				    </view>
					<image class="cancel-p" src="../../static/img/cancel.png" style="width:20px;height:20px" @click="cancel"></image>
				</view>
			</uni-popup>
            <uni-popup ref="less" type="center">
                <view class="nui-tip1" style="position:relative;margin:0">
                    <view style="background-color:white;opacity:1 ;width: 260px;height: 240px;" class="popup-v">
                        <view>
                            <image src="../../static/img/prompt2.png" style="width: 260px;height: 90px;position: relative;left: 50%;margin-left: -130px"></image>
                        </view>
                        <view style="color:white;font-size:15px;position: relative;top: -28%;left: 15px;">余额不足</view>
                        <view stye="font-size:14px">
                            <view>
                                <image class="payWarn" src="../../static/img/warn.png"></image>
                            </view>
                            <p style="margin:20px 0 0 30px;color:#323232;font-size:14px">钱包中的余额不足以支付此订单</p>
                            <view style="position: relative;top: 20px;display: flex;flex-direction: row;">
                                <button class="cancle" style="margin: 0 10px 0 40px;" @click="cancel">关闭</button>
                                <navigator url="/pages/index/recharge" hover-class="navigator-hover">
                                    <button class="recharge payless" style="margin: 0 30px 0 10px">去充值</button>
                                </navigator>
                            </view>
                        </view>
                     </view>
                     <image class="cancel-p" src="../../static/img/cancel.png" style="width:20px;height:20px" @click="cancel"></image>
                </view>
            </uni-popup>
             <uni-popup ref="success" type="center">
                <view class="nui-tip1" style="position:relative;margin:0">
                    <view style="background-color:white;opacity:1 ;width: 260px;height: 240px;" class="popup-v">
                        <view>
                            <image src="../../static/img/prompt2.png" style="width: 260px;height: 90px;position: relative;left: 50%;margin-left: -130px"></image>
                        </view>
                        <view style="color:white;font-size:15px;position: relative;top: -28%;left: 15px;">余额不足</view>
                        <view stye="font-size:14px">
                           <view style="position: absolute;left: 50%;margin-left: -45px;bottom: 50%;">
                                <image class="or-circle" style="width:90px;height:90px" src="../../static/img/circle.png"></image>
                                <image class="success" src="../../static/img/true.png"></image>
                            </view>
                            <h4 style="width: ：100px;position: relative;left: 50%;margin-left: -35px;">下单成功</h4>
                            <p style="margin-left:27%;margin-top:10px;color: #323232;font-size: 14px;">请等待陪练员接单</p>
                            <view style="position: relative;top: 20px;display: flex;flex-direction: row;">
                                <button class="back" style="margin: 0 10px 0 40px;color:#346CD5" @click="goHome">返回首页</button>
                                <navigator url="/pages/myInfor/orderDetails" hover-class="navigator-hover">
                                    <button class="recharge payless" style="margin: 0 30px 0 10px">查看订单</button>
                                </navigator>
                            </view>
                        </view>
                    </view>
                    <image class="cancel-p" src="../../static/img/cancel.png" style="width:20px;height:20px" @click="cancel"></image>
                </view>
            </uni-popup>
        </view>
    </view>
</view>
</template>

<script>
    import uniPopup from '@dcloudio/uni-ui/lib/uni-popup/uni-popup'
    export default{
        components:{
			uniPopup
		},
       data(){
           return {
               aera: [{name:'艾欧尼亚 '},{name: '祖安'}, {name:'诺克萨斯'}, {name:'班德尔城'}],
               index:uni.getStorageSync('index'),
               arrayStage: [{name:'青铜'},{name:'白银'},{name:'黄金'},{name:'铂金'},{name:'钻石'},{name:'大师'},{name:'王者'}],
               Stageindex:uni.getStorageSync('Stageindex'),
               role:uni.getStorageSync('role'),
               price:'60.00',
               num:uni.getStorageSync('pLNum') ,
               remain:'800.00'
           }
       } ,
       onLoad(){
       },
       methods:{
           // 弹框
			openPrompt() {  //打开弹框
				this.$refs.popupt.open()
            },
            cancel() {   //关闭弹框
                this.$refs.popupt.close();
                this.$refs.less.close();
                this.$refs.success.close();
            },
            confirmPay(){
                if(this.remain < this.price * this.num){
                    this.$refs.less.open();
                    this.$refs.popupt.close()
                }else{
                    this.$refs.success.open();
                    this.$refs.popupt.close()
                }
            },
            goHome(){
                uni.switchTab({
                url: '/pages/index/index'
            });
            console.log("跳转")
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
    line-height:3.4;
}
.total{
    color: #EEB357;
    position: absolute;
    top: 25%;
    margin-left: 15px;
}
.cancel-p{
	position: relative !important;
	top: 30px;
	left: 50% !important;
	margin: 0 0 0 -10px !important;
}
.recharge, .replay, .cancle,.back{   
    height: 30px;
    width:90px;
    font-size: 14px;
    border: 1px solid #346Cd5;
    line-height: 2;
    padding: 0 10px 0 10px;
}
.recharge,.cancle{
    color: #346CD5;
    float: left;
    margin: 0 15px 0 30px;
}
.replay ,.payless{
    color: #fff;
    background-color:#346Cd5 
}
.payWarn{
    width: 90px;
    height: 90px;
    position: absolute;
    left: 50%;
    margin-left: -45px;
    bottom: 50%;
    margin-bottom: -10px;
}
/* .or-circle{

} */
.success{
    width: 50px;
    height: 50px;
    position: absolute;
    right: 50%;
    margin-right: -25px;
    top: 50%;
    margin-top: -30px;
}
</style>