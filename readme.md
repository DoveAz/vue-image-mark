![](http://static.doveaz.xyz/img/20200602172637.png)



props

| name       | type   | default | required | description          |
| ---------- | ------ | ------- | -------- | -------------------- |
| imageSrc   | String |         | true     | 图片地址             |
| pointList  | Array  |         | true     | 点列表               |
| pointStyle | Object |         | false    | 附加到每个点上的样式 |

events

| name       | params                                  | descriptioin                                        |
| ---------- | --------------------------------------- | --------------------------------------------------- |
| add        | point {x:Number,y:Number,id:Number,...} | x,y均为百分比数值, 必须设置此方法才能在图片上添加点 |
| pointClick | point {x:Number,y:Number,id:Number,...} |                                                     |



```vue
<ImageMark imageSrc="http://static.doveaz.xyz/img/2d.jpg" :pointList="pointList" @add="handleAdd"></ImageMark>
```