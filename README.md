# HTML4
HTML
from html.parser import HTMLParser
from urllib.request import urlopen

class MyHTMLParser(HTMLParser):
    def __init__(self):
        super().__init__()
        self.recording = False
        self.copyright_text = ""
    
    def handle_starttag(self, tag, attrs):
        if tag == 'span':
            for attr in attrs:
                if attr[0] == 'title' and 'copyright' in attr[1]:
                    print(attr[1])


def testParser(url):
    content = urlopen(url).read().decode()
    parser = MyHTMLParser()
    parser.feed(content)

testParser('https://zapatopi.net/treeoctopus/')
from html.parser import HTMLParser
from urllib.request import urlopen

class DisplaySRCValuesContainingBook(HTMLParser):
    def __init__(self):
        super().__init__()
    
    def handle_starttag(self, tag, attrs):
        if tag == "img":
            for attr in attrs:
                if attr[0] == "src" and "book" in attr[1].lower():
                    print(attr[1])

def testSRCParser(url):
    content = urlopen(url).read().decode()
    parser = DisplaySRCValuesContainingBook()
    parser.feed(content)

testSRCParser('http://www.nytimes.com/')
#todo 3
#import os
#
#def printAllFilesInTest3Directory(directory):
#    for filename in os.listdir(directory):
#        file_path = os.path.join(directory, filename)
#        
#        if os.path.isdir(file_path):
#            printAllFilesInTest3Directory(file_path)
#        else:
#            print(file_path)
#
#printAllFilesInTest3Directory("test/test2/test3")
