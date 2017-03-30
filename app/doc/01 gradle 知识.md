
#### gradle 使用总结

> 资料来源: https://dongchuan.gitbooks.io/gradle-user-guide-/build_script_basics/task_dependencies.html



#### gradle 编程方式
/编译第一个function
task hello {
    doLast {
        println 'Hello world!'
    }
}

task hellofun << {
    println 'Hello world! Funs'
}

#### gradle 执行

> .gradlew -q hellofun

> .gradlew -q hello


#### gradle 依赖


```
task hello {
    doLast {
        println 'Hello world!'
    }
}

task hellofun << {
    println 'Hello world! Funs'
}


task intro(dependsOn: hello) << {
    println "I'm Gradle"
}
```
> 针对依赖的方法 . 先执行依赖的方法 后执行后面的 println

#### gradle 动态任务
```
4.times { counter ->
    task "task$counter" << {
       println( " Ia am task  number :$counter")
    }
}

```

> ./gradlew -q task1

> 输出u: Ia am task number :1



