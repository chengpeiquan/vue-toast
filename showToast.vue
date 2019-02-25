<template>
	<div class="common-toast">
		<div class="content">
			<p> 
				<span></span> 
			</p> 
		</div>
	</div>
</template>

<script>
const showToast = {
	install(Vue,options) {
		Vue.prototype.$showToast = function (text, time = 2000, callback) {
			document.querySelector(".common-toast").style.display = "block";
			const newToast = document.querySelector(".common-toast .content");
			newToast.querySelector("span").innerText = text;
			setTimeout((w,h)=>{
				w = newToast.offsetWidth;
				h = newToast.offsetHeight;
				newToast.style.marginTop = "-" + h/2 + "px";
				newToast.style.marginLeft = "-" + w/2 + "px";
			},10);
			setTimeout(()=>{
				document.querySelector(".common-toast").style.display = "none";
				if (typeof callback === "function"){
					callback();
				}
			},time);
		}
	}
}
export default showToast;
</script>

<style lang="stylus" scoped>
.common-toast
	display none
	position fixed
	top 0
	left 0
	width 100%
	height 100%
	background-color rgba(0,0,0,0.6)
	z-index 999998
	.content
		position absolute
		top 50%
		left 50%
		margin-top -1rem
		margin-left -3rem
		background-color rgba(0,0,0,0.4)
		box-shadow 0 0 10px rgba(0,0,0,0.2)
		color #fff
		text-align center
		border-radius 6px
		z-index 999999
		p
			display table-cell
			vertical-align middle
			width 6rem
			height 2rem
			box-sizing border-box
			padding 0.2rem
			overflow hidden
		span
			font-size 0.3865rem
			vertical-align middle
			color #fff
</style>