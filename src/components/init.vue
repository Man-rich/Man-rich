<template>
	<div class="nav">
		<ul>
			<li>
				<i class="icon iconfont icon-jishufuwu"></i>
				收藏栏
			</li>
			<li>
				<i class="icon iconfont icon-time-circle"></i>
				查看菜单
			</li>
			<li>
				<i class="icon iconfont icon-smile"></i>
				点击结算
			</li>
			<li>
				<i class="icon iconfont icon-plus-circle"></i>
				查看更多
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
    name:'come'
	}
</script>

<style>
 	.nav{
 		width: 5%;
 		height: 100%;
 		float: left;
 	}
 	.nav>ul>li>i{
 		display: block;
 		font-size: 25px;
 	}
 	.nav>ul>li{
 		width: 100%;
 		height: 50px;
 		border-bottom: 1px solid #78818A;
 		text-align: center;
 	}
 	.nav>ul>li>img{
 		width: 100%;
 		height: 50px;
 	}
 	
</style>