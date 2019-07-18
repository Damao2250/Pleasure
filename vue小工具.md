```js
/**
 * 存储localStorage
 */
export const setStore = (name, content) => {
	if (!name) return;
	if (typeof content !== 'string') {
		content = JSON.stringify(content);
	}
	window.localStorage.setItem(name, content);
}

/**
 * 获取localStorage
 */
export const getStore = name => {
	if (!name) return;
	return window.localStorage.getItem(name);
}

/**
 * 删除localStorage
 */
export const removeStore = name => {
	if (!name) return;
	window.localStorage.removeItem(name);
}


/**
 * 设置路由
 */
const router = new VueRouter({
  mode: 'hash',
  // mode: 'history',
  base: './',	//这个必配，是index.html所在的路径地址
  routes: [
    // 登录
    {
      path: '/login',
      name: 'login',
      component: () => import('@/views/login/login'),
    },
    // 首页
    {
      path: '/home',
      name: 'home',
      component: () => import('@/views/home/home'),
      // 二级路由
      children: [
        {
          path: '/dynamic',
          name: 'dynamic',
          component: () => import('@/views/dynamic/dynamic'),
          meta: { keepAlive: true } // 是否需要缓存
        }
      ]
    },
    {
      path: '/404',
      name: '404',
      component: () => import('@/views/404Page/404Page'),
    },
    //地址为空时跳转home页面
    {
      path: '',
      redirect: '/home'
    },
    {
      path: '/',
      redirect: '/home'
    },
    {
      path: '*',  // 匹配不到资源重定向到 "/"
      redirect: '404'
    }
  ]
})

```