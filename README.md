# ldr: 记事本, 紧迫性问题
提交所有数据之后, 改名字:  


Centos6.9升级glibc解决“libc.so.6: version GLIBC_2.14 not found”报错问题
https://blog.csdn.net/heylun/article/details/78833050


def word_youdao(word="ice"):
    import requests
    from bs4 import BeautifulSoup
    print('='*30)
    try:
        # 利用GET获取输入单词的网页信息
        url_yd = 'http://dict.youdao.com/w/%s/#keyfrom=dict2.top'%word
        r = requests.get(url=url_yd)
        # 利用BeautifulSoup将获取到的文本解析成HTML
        soup = BeautifulSoup(r.text, "lxml")
        # 获取字典的标签内容
        s = soup.find(class_='trans-container')('ul')[0]('li')
        # 输出字典的具体内容
        for item in s:
            if item.text:
                print(item.text)
    except Exception:
        print("Sorry, there is a error!\n")
        
        
# '''
# Created on 2018-5-26
# 
# @author: yaoshuangqi
# '''
import urllib.request
import urllib.parse
import json
 
class YoudaoFanyi():
    """
    有道词典API
    """
    VERSION = 1.1
    URL = 'http://fanyi.youdao.com/openapi.do'
    KEY_FROM = 'Dic-EVE'
    KEY = '975360059'
    TYPE = 'data'
    # 可选值xml, json
    DOC_TYPE = 'json'
    def translate(self, text):
        """
        翻译方法，传入要翻译的文本，返回结果字典
        """
        # 参数
        params = {'keyfrom': self.KEY_FROM, 'key': self.KEY, 'type': self.TYPE, 'doctype': self.DOC_TYPE, 'version': self.VERSION ,'q': text}
        resp = urllib.request.urlopen(self.URL, urllib.parse.urlencode(params).encode(encoding='utf_8'))
        data = resp.read().decode("utf_8")
        print('有道API翻译内容:%s'%data)
        return json.loads(data)
 
    def format_for_command(self, text):
        """
        为命令行格式化翻译结果
        """
        data = main(text)
        # TODO：格式化字符串
        if data:
            print('有道翻译：')
            print('\t原文本：', data.get('query', text)) 
            translation = data.get('translation',None)
            explains = data['basic']['explains']
            if translation: 
                for t in translation:
                    print('\t翻  译：', t)
                if explains:
                    print('\t解释：',explains)
            else:
                print('未找到该词')
def main(text):
    if text and text.strip() != '':
        return YoudaoFanyi().translate(text)

if __name__ == '__main__':
    while True:
        content = input('请输入翻译内容：')
        if content:
            YoudaoFanyi().format_for_command(content)
        else:
            print('有道翻译： \n\t提示：您已退出！！')
            break
