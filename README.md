# ldr: 记事本
提交所有数据之后, 改名字:  

## 对数坐标系的含义: `连同数据一起伸缩坐标轴`
plt.close("all")
x = np.linspace(1,110,11)
y = x
y2 = np.log(x)

fig, axes =plt.subplots(1,3, figsize=(12,4) )

axes[0].plot(x, y, "-o", linewidth=2)
axes[1].semilogy(y, "-o", linewidth = 2)
axes[2].plot(x, y2, "-o", linewidth = 2)

axes[0].set_ylim(1, 120) 
#y轴是对数坐标,数值不能为0或负值
axes[1].set_ylim(1, 120) 
axes[2].set_ylim(1, 5)
