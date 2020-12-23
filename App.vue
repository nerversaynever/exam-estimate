<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	@import "colorui/main.css";
	@import "colorui/icon.css";
	.submitBtn,
	.cancelBtn,
	.defaultBtn {
		color: #fff;
		text-align: center;
		border-radius: 8upx;
		background: #db6553;
		line-height: 100upx;
		font-size: 32upx;
		display: block;
	}
	
	.cancelBtn {
		background: #f0f0f0;
		color: #db6553;
	}
	
	.defaultBtn {
		background: #db6553;
	}
	.defultColor{
		color: #db6553!important;
	}
	/*每个页面公共css */
</style>
