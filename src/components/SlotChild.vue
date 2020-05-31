<template>
  <div class="slot-child">
	  <header>
		  <slot name="header" :userData="userInfo">header</slot>
	  </header>
	  <main>
		  <slot :userData="userInfo">default</slot>
	  </main>
	  <footer>
		  <slot name="footer" :userData="userInfo">footer</slot>
	  </footer>
  </div>
</template>

<script>
export default {
  name: 'SlotChild',
	data() {
    return {
      userInfo: {
        name: '张三',
	      age: '18',
	      say: 'Hello World'
      }
    }
	}
}
</script>

<style lang="scss">
	.slot-child {
		header, main, footer {
			box-sizing: border-box;
			border-bottom: 1px solid #ccc;
			padding: 10px 0;
		}
	}
</style>
