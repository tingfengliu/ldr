# ldr: 记事本
================================================================
================================================================
def dir2(obj, piece=None, exclued_upper=True, max_length=None):
    """以更友好的方式列出对象所包含的方法; piece为方法应含有的子串;"""
    ans = [i for i in dir(obj) if i[0] != "_"]
    if exclued_upper!=True:
        ans = [i for i in ans if i[0].islower()]
    if piece!=None:
        ans = [i for i in ans if i.find(piece)!=-1]
    if max_length!=None:
        ans = [i for i in ans if len(i) <= max_length]
    ##上述过程类似于一个管道, 满足参数条件就要执行一次清除##
    if len(ans) == 0:
        print(">> Nothing was found. >>>")
    else: return ans
    
