# ldr: 记事本
提交所有数据之后, 改名字:  

#给出一个数字: 十进制(二进制,八进制, 十六进制), 将其表示为其他进制, 然后表格的形式, 打印该数字的所有进制数;
#number是一个序列,打印表格, 否则该表格只有一行
def ibox(number):
    number_int = int(number)
    number_bin = bin(number)    
    number_oct = oct(number)    
    number_hex = hex(number)    
    print(number,":", number_int, number_bin, number_oct, number_hex)
ibox(11)
