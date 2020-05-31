<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
  <div class="home">

	  <div class="type-item">
		  <h1>Vue 2.6.0 起写法</h1>
		  <slot-child>
			  <!--
				具名插槽简写: <template #header>
				具名插槽带作用域插槽简写: <template #header="anyName">
				-->
			  <template #header="anyName">
				  姓名: {{anyName.userData.name}}
			  </template>

			  <!--
				默认插槽简写(什么都不用写, 但只允许一个默认插槽): <template>这句话会插入默认插槽</template>
				默认插槽带作用域简写: 想多了, 这是不可能的...
				默认插槽完整写法: <template v-slot:default>
				默认插槽带作用域完整写法: <template v-slot:default="anyName">
				-->
			  <template v-slot:default="anyName">
				  年龄: {{anyName.userData.age}}
			  </template>

			  <!--均支持解构赋值-->
			  <template v-slot:footer="{userData}">
				  说话: {{userData.say}}
			  </template>
		  </slot-child>

		  <span class="show-img" @click="show1 = !show1">
			  {{show1 ? "关闭" : "显示"}}代码解读
		  </span>
		  <img v-if="show1" src="../assets/show1.png"  alt=""/>
	  </div>

	  <div class="type-item">
		  <h1>Vue 2.6.0 之前兼容写法</h1>
		  <slot-child>
			  <!--
				具名插槽: <template slot="header">
				具名插槽带作用域插槽: <template slot="header" slot-scope="anyName">
				-->
			  <template slot="header" slot-scope="anyName">
				  姓名: {{anyName.userData.name}}
			  </template>

			  <!--
				默认插槽简写(什么都不用写, 但只允许一个默认插槽): <template>这句话会插入默认插槽</template>
				默认插槽带作用域: <template slot-scope="anyName">
				默认插槽完整写法: <template slot="default">
				默认插槽带作用域完整写法: <template slot="default" slot-scope="anyName">
				-->
			  <template slot="default" slot-scope="anyName">
				  年龄: {{anyName.userData.age}}
			  </template>

			  <!--均支持解构赋值-->
			  <template slot="footer" slot-scope="{userData}">
				  说话: {{userData.say}}
			  </template>
		  </slot-child>

		  <span class="show-img" @click="show2 = !show2">
			  {{show2 ? "关闭" : "显示"}}代码解读
		  </span>
		  <img v-if="show2" src="../assets/show2.png"  alt=""/>
	  </div>

	  <div class="type-item">
			<span class="show-img" @click="show3 = !show3">
			  {{show3 ? "关闭" : "显示"}}子组件代码
		  </span>
		  <img v-if="show3" src="../assets/show3.png"  alt=""/>
	  </div>

  </div>
</template>

<script>
  // @ is an alias to /src
  import SlotChild from "@/components/SlotChild.vue";

  export default {
	  name: 'Home',
	  components: {
		  SlotChild
	  },
	  data() {
	    return {
	      show1: false,
		    show2: false,
        show3: false
	    }
	  }
  }
</script>

<style lang="scss">
	.home {
		.type-item {
			padding: 15px;
			border: 5px solid turquoise;
			margin-bottom: 20px;
			.show-img {
				display: inline-block;
				padding: 20px 0;
				color: red;
				cursor: pointer;
				&:hover {
					text-decoration: underline;
				}
			}
			img {
				display: block;
			}
		}
	}
</style>
