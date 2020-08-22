# online-notifier-

import  requests
from bs4 import BeautifulSoup
from plyer import notification 
import time




result=requests.get('https://www.mohfw.gov.in/').text
soup=BeautifulSoup(result,'html.parser')
soup.encode('utf-8')
total_cases=soup.find('li',{'class':'bg-blue'}).get_text().strip()
print(total_cases)

def notifyy(notify_title,cases):
    notification.notify(title=notify_title,
                         message=cases,
                         timeout=5)

while True:
    notifyy("total cases of corona",total_cases)
    time.sleep(10)






