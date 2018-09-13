# d5
#datetime
from datetime import datetime
now=datetime.now()
print(now)
print(type(now))

dt=datetime(2017,4,25,3,28,10)
print(dt)

dt1=datetime(2015,3,28,4)
dt1.timestamp()

t = 1429417200.0
print(datetime.fromtimestamp(t))
print(datetime.utcfromtimestamp(t))

#strptime()
from datetime import datetime
day=datetime.strptime('2015-6-1 18:19:59','%Y-%m-%d %H:%M:%S')
print(day)

now=datetime.now()
print(now.strftime('%a, %b %d %H:%M'))

#timedelta
from datetime import datetime,timedelta
now=datetime.now()
now+timedelta(hours=10)
now+timedelta(days=1)
now=timedelta(days=3,hours=8)

#timezone
from datetime import datetime.timedelta,timezone
tz_utc_8=timezone(timedelta(hours=8))
now=datetime.now()
dt=now.replace(tzinfo=tz_utc_8)

#practice
import re
from datetime import datetime, timezone, timedelta
def to_timestamp(dt_str, tz_str):
    dt=datetime.strptime(dt_str,'%Y-%m-%d %H:%M:%S')
    tz_utc= timezone(timedelta(hours=int(tz_str[3:-3])))
    d = dt.replace(tzinfo=tz_utc)
    return d.timestamp()
    
#namedtuple
from collections import namedtuple
Point=namedtuple('Point',['x','y'])
p=Point(1,2)
p.x
p.y

#deque
from collections import deque
q=deque(['a','b','c'])
q.append('d')
q.appendleft('f')
q.popleft

#Counter
from collections import Counter
c=Counter()
for ch in 'programming':
    c[ch]=c[ch]+1
    
#base64
import base64
def safe_base64_decode(s):
    n=len(s)%4
    s=s+b'='*n
    return base64.b64decode(s)

#md5
db = {
    'michael': 'e10adc3949ba59abbe56e057f20f883e',
    'bob': '878ef96e86145580c38c87f0410ad153',
    'alice': '99b1c2188db85afee403b1536010c2c9'
}
import hashlib
def login(user,password):
    md=hashlib.md5()
    md.update(password.encode('utf-8'))
    return db[user]==md.hexdigest()
