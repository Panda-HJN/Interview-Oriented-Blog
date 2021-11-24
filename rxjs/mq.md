# 怎么用 rxjs 实现类似于消息队列的功能?
之前遇到个场景:   
不定时产生不定量的数据,   
消费端要定时按序消费固定个数的数据.所有数据都要被消费掉.  
rxjs 比较适合
```typescript
import { interval, zip, Subject } from 'rxjs';
import { bufferTime } from 'rxjs/operators';

    const source = new Subject();

    let count = 0;

    function start() {
      source.next(count++);
      setTimeout(() => {
        start();
      }, (Math.random() * 0.3 + 0.4) * 300);
    }

    start();

    zip(
      interval(3000),
      source.pipe(
        bufferTime(3000, null, 100)
      )
    ).subscribe(
      ([a, b]) => {
        console.log(new Date());
        console.log('a',a,'b',b);
      }
    );

```
