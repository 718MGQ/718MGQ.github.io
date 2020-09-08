---
title: 关于我
date: 2020-06-11 18:46:08
---
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <link rel="icon" href="<%= BASE_URL %>favicon.ico">
  <title><%= htmlWebpackPlugin.options.title %></title>
</head>

<body>
  <noscript>
    <strong>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work properly without JavaScript enabled.
      Please enable it to continue.</strong>
  </noscript>
  <div id="app">
    <div class="header_image_content"></div>
    <div class="user_name_content">Hi G.Miao</div>
    <br />
    <div class="user_info_content">
      <div>QQ: 1159950461</div>
      <div>WeChat: m1159950461</div>
      <div>Email: mgq_1996@163.com</div>
    </div>
    <br />
    <div class="bottom_button_content">
    	<div>
    		<div class="add_us_content"> </div>
    		<div class="wechat_content">加入我们</div>
    	</div>
	      <!-- <div>
	      	<div class="reward_us_content"></div> 
	      	<div class="wechat_content">打赏</div>
	      </div> -->
    </div>
     
  </div>
</body>

</html>
<script>

</script>
<style>
.header_image_content {
  width: 100px;
  height: 100px;
  background-image: url("/images/xhr.jpg");
  background-size: cover;
  border-radius: 50px;
  margin: auto auto 20px auto;
}
.user_name_content {
  font-size: 24px;
  font-weight: bold;
  line-height: 28px;
  text-align: center;
}
.wechat_content {
  font-size: 16px;
  font-weight: bold;
  line-height: 28px;
  text-align: center;
}

.user_info_content {
  color: cadetblue;
  text-align: center;
}

.bottom_button_content {
  display: flex;
  justify-content: center;
}

.add_us_content {
  width: 100px;
  height: 100px;
  background-image: url("/images/weChat.jpg");
  background-size: cover;
  display: inline-block;
  margin-right: 20px;
  margin-left: 20px;
  border-radius: 5px;
}

.reward_us_content {
  width: 100px;
  height: 100px;
  background-image: url("/images/money.png");
  background-size: cover;	
  display: inline-block;
  margin-left: 20px;
  margin-right: 20px;
  border-radius: 5px;
}
</style>