

## Labelme —— 深度学习图像分割任务

### 项目地址

https://github.com/wkentaro/labelme

### labelme常用命令

```
labelme 
# 直接打开labelme

labelme cat.jpg\
  --labels cat,eye
# 指定label list
  --labels labels.text
# 传入文件形式的label list

labelme_json_to_dataset cat.json
# 将json 文件转化为image和label(png)

labelme_draw_json cat.json 
# 可视化json文件
```
* 批量json转png  https://blog.csdn.net/qq_44770178/article/details/118802824
  
