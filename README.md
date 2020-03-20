# marquee


![image](https://github.com/warmilk/vue-marquee/blob/master/src/assets/Peek%202020-03-20%2016-17.gif)


components 目录下面的 marquee.vue 就是核心代码了，核心代码其实也就几行而已，让ul往左边滚动到容器尽头然后马上拽回来，之后又开始自动往左滚动，由于人眼有帧率识别极限，在被拽回来这一瞬间，只要li节点数足够多，人眼是没有感知的，就会有一直在无限往左滚动的错觉。

懒得上传到npm了，需要的欢迎自取封装

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```
