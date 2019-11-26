# UUID

## 作用
  UUID 的目的是让分布式系统中的所有元素，都能有唯一的辨识资讯，而不需要透过中央控制端来做辨识资讯的指定

## 重复几率
  ...

## 实际应用
> React's power lies in its robust reconciliation process. When we use JSX to create or update components, React creates its own virtual DOM. It compares this virtual DOM to the actual DOM in the browser, calculating the least number of changes necessary to update the actual DOM to match the virtual DOM. Sometimes we use multiple instances of the same component in the same spot. Such as the multiple instances of a 'TodoItem' component inside a 'TodoList' component. When this occurs, unique keys are very important, because they allow React to differentiate between these similar components, and hone in on any that may need to be updated individually, instead of re-rendering them all.

> React的力量在于强大的reconciliation流程。 当我们使用JSX创建或更新组件时，React会创建自己的虚拟DOM。 它将虚拟DOM与浏览器中的实际DOM进行比较，计算出更新实际DOM以匹配虚拟DOM所需的最少更改次数。 有时，我们在同一位置使用同一组件的多个实例。 例如“ TodoList”组件内的“ TodoItem”组件的多个实例。 发生这种情况时，唯一键非常重要，因为它们使React能够区分这些相似的组件，并专注于可能需要单独更新的任何组件，而不是重新渲染它们。

## 解决方案
  使用组件[react-uuid][react-uuid]
  ```
  import React from 'react'
  import uuid from 'react-uuid'

  const array = ['one', 'two', 'three']

  export const LineItem = item => <li key={uuid()}>{item}</li>

  export const List = () => array.map(item => <LineItem item={item} />)
  ```


[react-uuid]: https://www.npmjs.com/package/react-uuid 'react-uuid'