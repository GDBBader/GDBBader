---


title: 代码理解：van-checkbox 切换
date: 2021-09-02 09:29
tags: [vant,vue,JavaScript]
type:

---


## van-checkbox vue2代码

```html
<van-checkbox-group v-model="result">
  <van-cell-group>
    <van-cell
      v-for="(item, index) in list"
      clickable
      :key="item"
      :title="`复选框 ${item}`"
      @click="toggle(index)"
    >
      <template #right-icon>
        <van-checkbox :name="item" ref="checkboxes" />
      </template>
    </van-cell>
  </van-cell-group>
</van-checkbox-group>
```

```javascript
export default {
  data() {
    return {
      list: ['a', 'b'],
      result: [],
    };
  },
  methods: {
    toggle(index) {
      this.$refs.checkboxes[index].toggle();
    },
  },
};
```

- `this.$refs.checkboxes[index]`：因为checkboxes是在一个循环里，所有循环之后有多个，需要通过index去访问对应的checkboxes
- this.$refs.checkboxes[index].toggle()中的`toggle()`不是van-cell上的toggle()事件，而是van-checkbox上的组件实例方法。


## van-checkbox vue3代码

```html
<van-checkbox-group v-model="checked">
  <van-cell-group>
    <van-cell
      v-for="(item, index) in list"
      clickable
      :key="item"
      :title="`复选框 ${item}`"
      @click="toggle(index)"
    >
      <template #right-icon>
        <van-checkbox
          :name="item"
          :ref="el => checkboxRefs[index] = el"
          @click.stop
        />
      </template>
    </van-cell>
  </van-cell-group>
</van-checkbox-group>
```

```javascript
import { ref, onBeforeUpdate } from 'vue';

export default {
  setup() {
    const checked = ref([]);
    const checkboxRefs = ref([]);
    const toggle = (index) => {
      checkboxRefs.value[index].toggle();
    };

    onBeforeUpdate(() => {
      checkboxRefs.value = [];
    });

    return {
      list: ['a', 'b'],
      toggle,
      checked,
      checkboxRefs,
    };
  },
};
```

- `:ref="el => checkboxRefs[index] = el"` ：vue3的写法，作用就是将当前组件绑定到`checkboxRefs[index]`上，与vue2 中的自动生成类似

![[Pasted image 20210902103522.png]]


## 参考

1. [v-for 中的 Ref 数组 | Vue.js](https://v3.cn.vuejs.org/guide/migration/array-refs.html#%E8%BF%81%E7%A7%BB%E7%AD%96%E7%95%A5)
2. [Checkbox 复选框 - Vant](https://vant-contrib.gitee.io/vant/v3/#/zh-CN/checkbox#shui-ping-pai-lie)
3. [Vant - 轻量、可靠的移动端组件库](https://vant-contrib.gitee.io/vant/#/zh-CN/advanced-usage#zu-jian-shi-li-fang-fa)
4. [特殊 attribute | Vue.js](https://v3.cn.vuejs.org/api/special-attributes.html#ref)
