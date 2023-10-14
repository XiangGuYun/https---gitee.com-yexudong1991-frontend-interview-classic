下面是一个基本的示例，展示了 Vue 组件之间使用 **Props** 和 **Events** 通信的常见模式。

### 父组件

这个组件负责传递一个 prop 到子组件，并在子组件触发事件时做出响应。

```html
<template>
  <div>
    <h1>{{ messageFromChild }}</h1>
    <child-component 
      :parentMessage="parentMessage" 
      @childEvent="handleChildEvent"
    />
  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue';

export default {
  components: {
    ChildComponent
  },
  data() {
    return {
      parentMessage: 'Hello from parent', // 将被传递给子组件的数据
      messageFromChild: ''  // 用于接收从子组件传递过来的数据
    }
  },
  methods: {
    handleChildEvent(payload) {  // 处理子组件传递过来的事件和数据
      this.messageFromChild = payload;
    }
  }
}
</script>
```

### 子组件

这个组件接收一个来自父组件的 prop，并通过触发一个事件将一个消息发送回父组件。

```html
<template>
  <div>
    <h2>{{ parentMessage }}</h2> <!-- 显示从父组件接收的数据 -->
    <button @click="sendMessageToParent">Send Message to Parent</button> 
    <!-- 当按钮被点击时，触发sendMessageToParent方法 -->
  </div>
</template>

<script>
export default {
  props: {
    parentMessage: String  // 声明从父组件接收的prop
  },
  methods: {
    sendMessageToParent() {  
      // 当方法被调用时，触发一个自定义事件，同时传递一个数据(payload)给父组件
      this.$emit('childEvent', 'Hello from child');
    }
  }
}
</script>
```

**解析**

- **Props**：父组件通过`:parentMessage="parentMessage"`将其数据`parentMessage`传递到子组件。子组件通过在`props`选项中声明`parentMessage`来接收这个数据。

- **Events**：当子组件的按钮被点击时，`sendMessageToParent`方法被调用，进而触发名为`childEvent`的自定义事件，并传递一个字符串`'Hello from child'`作为参数。父组件监听这个事件`@childEvent="handleChildEvent"`，并定义了一个方法`handleChildEvent`来处理这个事件，该方法将接收到的消息（即传递的参数）赋值给`messageFromChild`，显示在父组件的模板中。


***

### 追问：父组件接收子组件传值的方式能否用.sync修饰符简化？如果可以，请给出简化后的父组件代码，并给出注释。

是的，使用 .sync 修饰符可以使得父子组件间的数据同步更为便捷。.sync 修饰符允许我们在一个子组件中修改 prop 的值，而不直接影响父组件的数据状态。

```html
<template>
  <div>
    <h1>{{ messageFromChild }}</h1>
    <child-component :parentMessage.sync="parentMessage" />
    <!-- 使用 .sync 修饰符进行双向数据绑定 -->
  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue';

export default {
  components: {
    ChildComponent
  },
  data() {
    return {
      parentMessage: 'Hello from parent', // 将被传递给子组件的数据
    }
  }
}
</script>
```