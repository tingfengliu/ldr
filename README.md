# ldr: 记事本
提交所有数据之后, 改名字:  



木里(503,623,莫林社区方向) => 横泾(502,621,62,浦庄方向) => 东山首末站:1000m雨花胜境, 1000m => 将军街(629,东山交警大队) => 东山陆港桥(629) =>桥头(502,621,62)

def conflict(state,nextX):
    """state为之前的状态, nextX为下一个状态, 
    该函数用于判断下一个状态是否与已有状态冲突"""
    nextY = len(state)
    for i in range(nextY):
        if abs(state[i]-nextX) in (0, nextY-i):
            return True
    return False
def queens(num=8,state=()):
    for pos in range(num):
        if not conflict(state,pos):
            """该状态与已有状态不冲突, 并且该状态是最后一个状态"""
            if len(state)==num-1:
                yield (pos,)
            else: #该状态不是最后一个状态, 必须返回一个可继续作为queens()的参数的状态
                for result in queens(num, state+(pos,)):
                    yield (pos,) + result
