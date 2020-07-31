<template>
	<view class="content">
		<image src="../../static/img/bg1.png" style="height: 100%;width: 100%;"></image>
		<view class="title">
			<image src="../../static/img/logo.png"></image>
		</view>
		<view class="information">
			<image src="../../static/img/border.png"></image>
			<view class="info">
				<view class="p_infor" style="margin-left: 35px;">
					<picker @change="bindIndexChange" :value="index" :range="array" range-key="name">
						 大区<view class="uni-input" >{{array[index].name}}
							 <image src="../../static/img/JT.png" ></image>
						 </view>
					</picker>
				</view>
				<view class="p_infor">
					<picker @change="bindStrageChange" :value="Stageindex" :range="arrayStage" range-key="name">
						 当前段位<view class="uni-input" style="width:55%">{{arrayStage[Stageindex].name}}
							 <image src="../../static/img/JT.png" ></image>
						 </view>
					    
					</picker>
				</view>
				<view class="p_infor">
				角色名称 <input class="in-input" type="text" v-model="role" placeholder="请输入你的角色名称" @input="getRole"/>
				</view>
				<view class="p_infor">
					陪练盘数 <input class="in-input" type="text" v-model="plNum" placeholder="请输入陪练盘数" @input="getPlNum"/>
				</view>
				<view class="p_infor" style="margin-left: 15px;">
					<span style="position: relative;bottom:23px">陪练员</span>
					 <checkbox-group class="checkbox-group" @change="checkboxChange">
					     <label  v-for="item in items" :key="item.value" style="font-size:15px">
								<checkbox :value="item.name" :checked="item.checked" />{{item.name}} <br>
					     </label>
					</checkbox-group><br>
					<input class="in-input" type="text" v-model="plCard" placeholder="请输入陪练编号" style="width: 60%;left: 25%;" @input="getPlCard"/>
				</view>
				<view class="p_infor">
					联系方式<input class="in-input" type="text" v-model="phomeNum" placeholder="请输入联系方式" @input="getPhoneNum"/>
				</view>
				<!-- 按钮 -->
				<view>
					<button class="b_next_button" @click="openPrompt">下一步</button>
					<uni-popup ref="popupt" type="center">
						<view class="nui-tip1" style="position:relative;margin:0">
							<view style="background-color:white;opacity:1 ;width: 230px;height: 190px;" class="popup-v">
								<view>
									<image src="../../static/img/prompt.png" style="width: 230px;height: 70px;position: relative;left: 50%;margin-left: -115px"></image>
								</view>
								<view style="color:white;font-size:15px;position:relative;top:-31%;left:15px;">温馨提示</view>
								<view >
									<h6 style="position: relative;left: 15px;">营业时间</h6><br>
									<view style="position:relative;top:5px">
										<image src="../../static/img/time.png" style="width:15px;height:15px;margin:0;padding:0;position: relative;left: 15px;top: 2px;"></image>
										<text style="position:relative;left:20px;font-size:15px">9:00-23:00</text><br>
										<view style="width:195px;position: relative;left: 15px;">
											<text style="color:#C8C8C8;font-size:10px">如不在工作时间段下单，订单接单可能稍有延迟， 请耐心等待至工作时间</text>
										</view>
									</view>
								</view>
							</view>
							<!-- 页面跳转 -->
							<navigator url="/pages/index/orderConfirm?title=navigate" hover-class="navigator-hover">
								<image class="cancel-p" src="../../static/img/cancel.png" style="width:20px;height:20px" @click="submitInfor"></image>
							</navigator>
						</view>
					</uni-popup>
				</view>
			</view>
		</view>
	</view>
	
</template>

<script>
	import uniPopup from '@dcloudio/uni-ui/lib/uni-popup/uni-popup'
	export default {
		components:{
			uniPopup
		},
		data() {
			return {
				title: '英雄联盟',
				titleLog:'LEAGUE  LEGENDS',
				role:'',
				pLNum:'',
				// picked:[],
				items:[
					{name:'随机陪练员'},
					{name:'指定陪练员'}
				],
				array: [{name:'艾欧尼亚 '},{name: '祖安'}, {name:'诺克萨斯'}, {name:'班德尔城'}],
				index: 0,	
				arrayStage: [{name:'青铜'},{name:'白银'},{name:'黄金'},{name:'铂金'},{name:'钻石'},{name:'大师'},{name:'王者'}],
				Stageindex:0,
				plCard:'',
				phoneNum:''
				// showtip:false,
			}
		},
		onLoad() {
		},
		methods: {
			checkboxChange: function (e) {
				this.checked=e.detail.value			//获取复选框的数组值
				this.checked=this.checked.join(",") 
			},
			// 获取当前下拉列表picker的值
			bindIndexChange: function(e) {
				this.index = e.detail.value
			},
			bindStrageChange: function(e) {
				this.Stageindex = e.detail.value
			},
			// 弹框
			openPrompt() {
				this.$refs.popupt.open()
			},
			// 获取input的值
			 getRole:function(event){  
            // 绕过v-model 获取input输入框的值  
            this.role = event.detail.value   
			},
			getPlNum:function(event){   
            this.plNum = event.detail.value   
			},
			getPlCard:function(event){   
            this.plCard = event.detail.value   
			},
			getPhoneNum:function(event){   
            this.phoneNum = event.detail.value   
			},
			// 缓存数据
			submitInfor:function(){
				uni.setStorageSync('role', this.role);//存储一个字符传值
				uni.setStorageSync('pLNum', this.plNum);
				uni.setStorageSync('index', this.index);
				uni.setStorageSync('Stageindex', this.Stageindex);
				uni.setStorageSync('plCard', this.plCard);
				uni.setStorageSync('checked', this.checked);
				uni.setStorageSync('phoneNum', this.phoneNum);
			}
		}
	}
</script>

<style>
	page{
		height: 100%;
	}
	.content {
		position: relative;
		background-color: #000048;
		width: 100%;
		height: 100%;
		
	}
	.title{
		position: absolute;
		top:5%;
		left: 50%;
		margin: 0 0 0 -80px;
	}
	.title image{
		width: 167px;
		height: 60px;
	}
	.information{
		width:100%;
		height: 75%;
		position: absolute;
		top:17%;
	}
	.information image{
		width:80%;
		height: 105%;
		position: absolute;
		left: 50%;
		margin: 0 0 0 -40%;
	}
	.info{
		position: absolute;
		left: 15%;
		top:5%;
	}
	.p_infor{
		color: #FAD154;
		font-size: 17px;
		margin-top: 10px;
	}
	.uni-input{
		display:inline-block;
		color:white;
		width: 65%;
		position: relative;
		left: 10px;
		font-size: 15px;
		border-bottom:1px solid #FFFFFF
	}
	.uni-input image{
		width:13px;
		height:8px;
		left: 130%; 
		top:10px;
	}
	.in-input{
		display: inline-block;
		position: relative;
		top:5px;
		left: 10px;
		border-bottom: 1px solid #FFFFFF;
		width: 55%;
		color: #FFFFFF;
		font-size: 15px;
	}
	checkbox .wx-checkbox-input{
		width: 20px;
		height: 20px;
		border-radius: 5px;
		background-color: inherit;
	} 
	.checkbox-group{
		display: inline-block;
		margin-top: 5px;
		margin-left: 12px;
		color: #FFFFFF;
	}
	.b_next_button{
		background-color: #346CD5;
		height: 30px;
		line-height: 1.7;
		color: #fff;
		width: 80%;
		position: relative;
		top: 20px;
		left: 50%;
		margin-left: -45%;
	}
	.cancel-p{
		position: relative !important;
		top: 30px;
		left: 50% !important;
		margin: 0 0 0 -10px !important;
	}
</style>
