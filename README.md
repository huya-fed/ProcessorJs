# js多线程处理器

* 使用示例
```javascript
var processor = new Processor(2)

processor.process(function(release, i){
    console.log('processor-'+ i +': taskA-start')

    setTimeout(function(){
        console.log('processor-'+ i +': taskA-end')
        release()
    }, 5000)
})

processor.process(function(release, i){
    console.log('processor-'+ i +': taskB-start')

    setTimeout(function(){
        console.log('processor-'+ i +': taskB-end')
        release()
    }, 2000)
})


processor.process(function(release, i){
    console.log('processor-'+ i +': taskC-start')

    setTimeout(function(){
        console.log('processor-'+ i +': taskC-end')
        release()
    }, 2000)
})

输出:
processor-0: taskA-start
processor-1: taskB-start
processor-1: taskB-end
processor-1: taskC-start
processor-1: taskC-end
processor-0: taskA-end
```