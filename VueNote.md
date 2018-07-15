# Vue 知识点

1. Props，methods， data 和 computed 的初始化都是在 beforeCreated 和 created 之间完成的。
2. click事件：.stop .prevent .capture .self .once .passive

* prevent：使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。因此，用 v-on:click.prevent.self 会阻止所有的点击，而 v-on:click.self.prevent 只会阻止对元素自身的点击。
* passive ：修饰符尤其能够提升移动端的性能。不要把 .passive 和 .prevent 一起使用，因为 .prevent 将会被忽略，同时浏览器可能会向你展示一个警告。请记住，.passive 会告诉浏览器你不想阻止事件的默认行为。
* stop ：组织点击事件冒泡
* capture ：点击obj4的时候，弹出的顺序为：obj1、obj2、obj4、obj3；
                由于1，2有修饰符，故而先触发事件，然后就是4本身触发，最后冒泡事件。

		<div id="obj1" v-on:click.capture="doc">
	      obj1
	      <div id="obj2" v-on:click.capture="doc">
	        obj2
	        <div id="obj3" v-on:click="doc">
	          obj3
	          <div id="obj4" v-on:click="doc">obj4</div>
           </div>
         </div>
      </div>
     
	                
		                


                