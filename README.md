itools
======

ios平台

源码最近会传上，因为git不怎么会用，熟悉中。


private var AppID:int = 1;
private var AppKey:String = "xxxxxxxxxxxxxxxxxxxx";
private var uid:String;
private var session:String;

XiawuANEHelper.getInstance().setCallBack(aneHandler);//设置回调函数

XiawuANEHelper.getInstance().itoosSDK.initSDK(AppID,AppKey,true,false);//初始化，appid和appkey 平台会给你
XiawuANEHelper.getInstance().itoosSDK.login();//登录弹窗
//money String类型  单位 元   ，orderID String订单id,你可以把服务器id和uid拼接进去
XiawuANEHelper.getInstance().itoosSDK.pay(money,orderID);//购买
//为什么 用户中心 还是 login，因为 有个参数 true啊 ，ios ane 有个 坑，以后会解释
XiawuANEHelper.getInstance().itoosSDK.login(true);//弹出用户中心




protected function aneHandler(code:String,level:String):void
{
	switch(code)
	{
		case "login_ane_sucess":
			var arr:Array = String(level).split(";");
			uid= arr[0];//用户唯一识别，uid
			session = arr[1];//token验证
			break;
		case "PAY_ANE_SUCESS":
			//支付成功
			break;
		case "logout_ane_sucess":
			//注销
			break;
	}
}
