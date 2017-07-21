# vue

> Contextmenu component for vue2

## Use Setup

# install vue-contextmenu
npm install vue-contextmenu --save

# Vue mount
	// mount with component
	import VueContextMenu form 'vue-contextmenu'
	import from 'vue-context/style/css/font-awesome.min.css' // use font-awesome icon (http://fontawesome.io/)

	export default {
		components: {
			VueContextMenu
		}
	}
# Use in SPA
	<template>
	  <div id="app" @contextmenu="showMenu" style="width: 100px;height: 100px;background: red;">
	    <vue-context-menu :contextMenuData="contextMenuData"
		                  @savedata="savedata"
		                  @newdata="newdata">
	    </vue-context-menu>
	  </div>
	</template>
	<script>
	  import VueContextMenu from 'vue-contextmenu'
	  import 'vue-contextmenu/style/css/font-awesome.min.css'
	  export default {
	    name: 'app',
	    components: {
	      VueContextMenu
	    },
	    data () {
	      return {
	      	// contextmenu data (菜单数据)
	        contextMenuData: {
	        // The coordinates of the display(菜单显示的位置)
	          axios: {
	            x: null,
	            y: null
	          },
	        // Menu options (菜单选项)
	          menulists: [
	            {
	              fnHandler: 'savedata', // Binding events(绑定事件)
	              icoName: 'fa fa-home fa-fw', // icon (icon图标 )
	              btnName: 'Save' // The name of the menu option (菜单名称)
	            },
	            {
	              fnHandler: 'newdata',
	              icoName: 'fa fa-home fa-fw',
	              btnName: 'New'
	            }
	          ]
	        }
	      }
	    },
	    methods: {
	      showMenu () {
	        event.preventDefault()
	        var x = event.pageX
	        var y = event.pageY
	        // Get the current location
	        this.contextMenuData.axios = {
	          x, y
	        }
	      },
	      savedata () {
	      	alert(1)
	      },
	      newdata () {
	      	console.log('newdata!')
	      }
	    }
	  }
	</script>
# Use in SPA(List Rendering)
    <template>
      <div>
        <div @contextmenu="showMenu(index)"
             style="width: 100px;height: 100px;background: red;margin-top: 20px;"
             v-for="(n, index) in 4" :key="n" >
             <vue-context-menu :contextMenuData="contextMenuData"
                               :transferIndex="transferIndex"
                               @savedata="savedata(index)"
                               @newdata="newdata"></vue-context-menu>
        </div>
      </div>
    </template>
    <script>
      import VueContextMenu from 'vue-contextmenu'
      import 'vue-contextmenu/style/css/font-awesome.min.css'
      export default {
        name: 'app',
        components: {
          VueContextMenu
        },
        data () {
          return {
            transferIndex: null, //Show the menu that was clicked
            contextMenuData: {
              axios: {
                x: null,
                y: null
              },
              menulists: [
                {
                  fnHandler: 'savedata',
                  icoName: 'fa fa-home fa-fw',
                  btnName: 'Save'
                },
                {
                  fnHandler: 'newdata',
                  icoName: 'fa fa-home fa-fw',
                  btnName: 'New'
                }
              ]
            }
          }
        },
        methods: {
          showMenu (index) {
            this.transferIndex = index //tranfer index to child component
            event.preventDefault()
            var x = event.pageX
            var y = event.pageY
            this.contextMenuData.axios = {
              x, y
            }
          },
          savedata (e) {
            console.log('click:' + e)
          },
          newdata () {
            console.log(2222)
          }
        }
      }
    </script>
# Email
    xxnmiss@163.com
# Test demo(use in spa)
![Image text](https://raw.githubusercontent.com/chIIC/vue-contextmenu/master/test.gif)
#Test demo(use in apa(List Rendering))
![Image text](https://raw.githubusercontent.com/chIIC/vue-contextmenu/master/test1.gif)





