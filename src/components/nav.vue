<template>
	<div class="nav_container">
		<div class="menu">
			<el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect" :active-text-color="activeColor" menu-trigger="hover">
			  <el-menu-item :index="erp_nav.erpmain.url">{{erp_nav.erpmain.name}}</el-menu-item>
				<el-submenu index="2">
			    <template slot="title">{{erp_nav.nowpage}}</template>
			    <el-submenu v-for="item1 in erp_nav.children" :index="item1.url" :key="item1.url">
			      <template slot="title">{{item1.name}}</template>
			      <el-menu-item v-for="item2 in item1.children" :index="item2.url" :key="item2.url">{{item2.name}}</el-menu-item>
			    </el-submenu>
			  </el-submenu>
			</el-menu>
			<div class="line"></div> 
		</div> 
	</div>
</template>

<script>
export default {
	name: 'sd-nav',
  	data () {
	    return {
	    activeColor:'#9b1700',
	    activeIndex: 'erpmain',
        erp_nav:{
        	nowpage:"导航",
        	erpmain:{
        		name:"首页",
        		url:"erpmain"
        	},
        	children:[{
        		name:"采购系统",
        		url:"cgxt",
        		children:[
	        	{
	        		name:"采购开单",
	        		url:"cgkd"
	        	},
	        	{
	        		name:"采购订单",
	        		url:"cgdd"
	        	}]
	        },
        	{
        		name:"销售系统",
        		url:"xsxt",
        		children:[{
        		name:"销售开单",
        		url:"xskd"
	        	},
	        	{
	        		name:"销售订单",
	        		url:"xsdd"
	        	}]
        	}]
        }
      };
	},
    methods: {
      handleSelect(key, keyPath) {
      	this.$parent.nowcomponent = key;
      }
    }
}
</script>
<style lang="less">
	@import '../style/mixin';
	.el-cascader{
		line-height: 60px;
	}
	.el-menu--horizontal>.el-menu-item,.el-menu--horizontal>.el-submenu .el-submenu__title{
		height: 40px;
		line-height: 40px;
	}
</style>