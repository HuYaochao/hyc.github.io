---
layout: post
title: "W-VueRouter"
date: 2024-7-29
tags: [vue3]
comments: true
author: hyc
---

# 路由是什么？

路由（Routing）是现代前端开发中的一个重要概念，它指的是根据用户请求的 URL 地址，将用户导航到特定的页面或组件。在单页面应用（Single Page Application，SPA）中，路由主要负责在用户界面之间切换，而无需重新加载整个页面，从而提升用户体验。

## 路由的核心概念

1. **路由表（Route Table）**：定义 URL 路径与组件之间的映射关系。例如，在 Vue.js 中，路由表是一个数组，其中每个元素都是一个路由对象，包含路径和组件等信息。

2. **路径（Path）**：用户在浏览器地址栏中输入的 URL 部分。路径通常与组件一一对应，用于决定在不同路径下展示哪个组件。

3. **组件（Component）**：路由指向的具体视图或页面。每当用户导航到特定路径时，路由器会加载并渲染对应的组件。

4. **路由器（Router）**：前端框架中的路由管理器，用于处理 URL 变化并渲染相应的组件。在 Vue.js 中，Vue Router 是一个官方插件，用于实现路由功能。

5. **导航守卫（Navigation Guards）**：一系列用于拦截导航的回调函数，允许在导航前、导航后或导航过程中执行一些逻辑，如权限检查或数据加载。

在主组件中使用 `<router-link>` 组件创建导航链接，并使用 `<router-view>` 组件显示当前路由匹配的组件：

# 组合式与选项式的区别

在 Vue 3 中，有两种主要的组件定义方式：选项式 API 和组合式 API。它们在编写方式和逻辑组织上有所不同，各有优缺点。下面详细解释它们的区别。

## 选项式 API（Options API）

选项式 API 是 Vue 2 及之前版本中使用的主要编程风格。它通过选项对象来定义组件的逻辑部分，如 `data`、`methods`、`computed`、`watch` 等。

### 特点

- **结构化**：逻辑通过特定选项分离，例如 `data`、`methods`、`computed` 等。
- **易于理解**：适合新手，易于理解和上手。
- **代码分散**：同一功能的逻辑可能分散在不同的选项中，随着组件复杂度增加，代码管理变得困难。

## 组合式 API（Composition API）

组合式 API 是 Vue 3 引入的一种新的编程风格。它通过函数组合来组织组件的逻辑部分，通常使用 `setup` 函数和 Vue 的响应式工具（如 `ref`、`reactive`、`computed`、`watch` 等）。

### 特点

- **逻辑聚合**：同一功能的相关逻辑可以聚合在一起，代码更容易维护和重用。
- **更强的灵活性**：能够更灵活地组织和复用逻辑代码，适合复杂组件和大型应用。
- **学习曲线**：对新手来说，可能需要一些时间来适应组合式 API 的新概念和用法。

## 选项式 API 与组合式 API 的对比

| 特点     | 选项式 API                         | 组合式 API               |
| -------- | ---------------------------------- | ------------------------ |
| 逻辑组织 | 按选项分离（`data`、`methods` 等） | 按功能组合，逻辑聚合     |
| 易学性   | 更容易理解和上手                   | 学习曲线较陡峭           |
| 代码复用 | 较难复用，逻辑分散                 | 更容易复用，逻辑集中     |
| 适用场景 | 适合简单和中等复杂度的组件         | 适合复杂组件和大型应用   |
| Vue 版本 | Vue 2 及之前主要使用               | Vue 3 引入，适用于 Vue 3 |

选项式 API 和组合式 API 各有优劣，选项式 API 更加直观易懂，适合简单组件和初学者；而组合式 API 提供了更大的灵活性和复用性，适合复杂组件和大型项目。在 Vue 3 中，两者可以混合使用，根据具体需求选择最合适的编程方式。

# 路由传值有哪几种方式

在 Vue.js 中，路由传值有几种常见的方式，包括通过路径参数、查询参数和路由元数据等。每种方式都有其适用的场景和特点。

### 1. 路径参数（Path Parameters）

路径参数是 URL 路径的一部分，通常用于需要唯一标识资源的情况，比如用户 ID、文章 ID 等。

#### 定义路由

在定义路由时，可以使用冒号 `:` 来表示路径参数：

```javascript
const routes = [
  {
    path: '/user/:id',
    component: User
  }
];
```

#### 访问路径参数

在组件中，可以通过 `this.$route.params` 来访问路径参数：

```vue
<template>
  <div>
    <p>User ID: {{ userId }}</p>
  </div>
</template>

<script>
export default {
  computed: {
    userId() {
      return this.$route.params.id;
    }
  }
};
</script>
```

#### 示例

访问 URL `/user/123`，`this.$route.params.id` 将返回 `123`。

### 2. 查询参数（Query Parameters）

查询参数是 URL 中以 `?` 开头的一部分，通常用于过滤、排序等非关键数据的传递。

#### 定义路由

查询参数不需要在路由配置中显式定义：

```javascript
const routes = [
  {
    path: '/search',
    component: Search
  }
];
```

#### 传递查询参数

可以通过路由跳转时传递查询参数：

```vue
<template>
  <div>
    <button @click="search">Search</button>
  </div>
</template>

<script>
export default {
  methods: {
    search() {
      this.$router.push({ path: '/search', query: { q: 'vue' } });
    }
  }
};
</script>
```

#### 访问查询参数

在组件中，可以通过 `this.$route.query` 来访问查询参数：

```vue
<template>
  <div>
    <p>Query: {{ query }}</p>
  </div>
</template>

<script>
export default {
  computed: {
    query() {
      return this.$route.query.q;
    }
  }
};
</script>
```

#### 示例

访问 URL `/search?q=vue`，`this.$route.query.q` 将返回 `vue`。

### 3. 路由元数据（Route Meta）

路由元数据是与路由关联的自定义数据，可以在路由配置中定义，用于控制路由的行为，比如权限控制等。

#### 定义路由

在路由配置中定义 `meta` 字段：

```javascript
const routes = [
  {
    path: '/dashboard',
    component: Dashboard,
    meta: { requiresAuth: true }
  }
];
```

#### 访问路由元数据

在组件中，可以通过 `this.$route.meta` 来访问元数据：

```vue
<template>
  <div>
    <p v-if="requiresAuth">This page requires authentication</p>
  </div>
</template>

<script>
export default {
  computed: {
    requiresAuth() {
      return this.$route.meta.requiresAuth;
    }
  }
};
</script>
```

#### 示例

如果当前路由的 `meta` 中有 `requiresAuth` 字段，`this.$route.meta.requiresAuth` 将返回 `true`。

### 4. 命名视图（Named Views）

命名视图允许在同一路由下同时显示多个视图，通常用于布局中需要多个不同组件同时展示的情况。

### 5. 路由导航守卫（Navigation Guards）

导航守卫可以在路由切换时进行一些逻辑处理，比如传递数据或检查权限。

#### 定义导航守卫

可以在全局、单个路由或组件内定义导航守卫：

```javascript
const router = createRouter({
  history: createWebHistory(),
  routes
});

router.beforeEach((to, from, next) => {
  if (to.meta.requiresAuth && !isAuthenticated()) {
    next('/login');
  } else {
    next();
  }
});
```

### 总结

- **路径参数**：适用于唯一标识资源的情况。
- **查询参数**：适用于非关键数据的传递，如过滤和排序。
- **路由元数据**：适用于控制路由行为的自定义数据，如权限控制。
- **命名视图**：适用于需要在同一路由下显示多个视图的情况。
- **导航守卫**：适用于在路由切换时进行逻辑处理，如数据传递和权限检查。

# 侦听器，计算属性，methods之间的关联和区别

在 Vue.js 中，侦听器（watchers）、计算属性（computed properties）、方法（methods）是三种不同的功能，它们各自有不同的用途和特点。在开发中，合理使用这些功能可以提高代码的可读性和效率。下面详细介绍它们的关联和区别。

### 1. 侦听器（Watchers）

侦听器用于监控数据的变化，并在数据变化时执行特定的逻辑。这对于需要在数据变化时执行异步操作或有较大开销的操作非常有用。

#### 使用场景

- 需要在数据变化时执行异步操作，如 API 请求。
- 需要在数据变化时执行开销较大的操作。
- 需要执行逻辑处理，而不仅仅是简单的计算。

### 2. 计算属性（Computed Properties）

计算属性是基于现有数据进行计算，并且会根据其依赖项的变化自动缓存和更新。计算属性的结果会被缓存，只有在依赖的数据发生变化时才会重新计算。

#### 使用场景

- 需要基于现有数据进行衍生计算。
- 需要计算的结果依赖于多个数据源。
- 希望避免重复计算，通过缓存提高性能。

### 3. 方法（Methods）

方法是定义在 `methods` 选项中的函数，通常用于处理用户交互、事件处理和不需要缓存的计算。与计算属性不同，方法在每次调用时都会重新执行。

#### 使用场景

- 处理用户交互和事件。
- 执行不需要缓存的计算或逻辑处理。
- 在模板中调用带有参数的函数。

### 关联和区别

| 特点           | 侦听器（Watchers）         | 计算属性（Computed Properties）    | 方法（Methods）                              |
| -------------- | -------------------------- | ---------------------------------- | -------------------------------------------- |
| 定义位置       | `watch` 选项               | `computed` 选项                    | `methods` 选项                               |
| 主要用途       | 监控数据变化并执行逻辑     | 基于现有数据进行衍生计算并缓存结果 | 处理用户交互、事件和不需要缓存的计算         |
| 是否缓存       | 否（每次数据变化都会触发） | 是（依赖项不变时返回缓存结果）     | 否（每次调用都会重新执行）                   |
| 使用场景       | 异步操作、开销较大的操作   | 依赖多个数据源的计算、避免重复计算 | 事件处理、调用带参数的函数、不需要缓存的计算 |
| 模板中调用方式 | 不直接在模板中调用         | 作为属性在模板中直接使用           | 作为函数在模板中调用                         |
| 参数支持       | 支持，监控具体数据的变化   | 不直接支持参数传递                 | 支持参数传递                                 |

### 总结

- **侦听器**适合需要在数据变化时执行异步操作或复杂逻辑的场景，提供了对数据变化的细粒度控制。
- **计算属性**适合需要基于现有数据进行计算并希望结果被缓存的场景，提供了性能优化的途径。
- **方法**适合处理用户交互和事件，以及不需要缓存的计算逻辑，提供了灵活的函数调用方式。

# Vue3中的生命周期函数有哪些，并解释每个函数的作用？

在 Vue 3 中，生命周期函数用于在组件的不同阶段执行特定的逻辑。在选项式 API 和组合式 API 中，生命周期函数的定义和使用方式有所不同。下面是它们的对比列表以及每个函数的作用解释。

### 选项式 API（Options API）

| 生命周期钩子    | 作用                                                         |
| --------------- | ------------------------------------------------------------ |
| `beforeCreate`  | 实例初始化之后，数据观测和事件配置之前调用。通常用于在组件实例化之前进行一些初始化任务。 |
| `created`       | 实例创建完成后调用，此时可以访问数据和事件，但组件尚未挂载到 DOM。通常用于初始化数据或发送网络请求。 |
| `beforeMount`   | 在挂载开始之前被调用，相关的 `render` 函数首次被调用。通常用于在初次渲染之前执行一些准备工作。 |
| `mounted`       | 挂载完成后调用，此时组件已经被渲染到 DOM。通常用于操作 DOM 或初始化与 DOM 相关的第三方库。 |
| `beforeUpdate`  | 数据变化导致的重新渲染之前调用。通常用于在组件更新之前执行一些任务。 |
| `updated`       | 由于数据变化导致的虚拟 DOM 重新渲染和打补丁之后调用。通常用于在组件更新后执行一些任务。 |
| `beforeUnmount` | 组件实例卸载之前调用。通常用于在组件被移除之前执行一些清理工作。 |
| `unmounted`     | 组件实例卸载之后调用。通常用于清理副作用（如定时器、事件监听等）。 |

### 组合式 API（Composition API）

在组合式 API 中，使用 Vue 3 提供的钩子函数来处理生命周期事件。这些函数需要在 `setup` 函数内调用。

| 生命周期钩子    | 对应组合式 API 的钩子函数                    | 作用                                                         |
| --------------- | -------------------------------------------- | ------------------------------------------------------------ |
| `beforeCreate`  | 不需要（setup 已经是 beforeCreate 之后调用） | 组合式 API 中没有对应的钩子函数，因为 `setup` 函数已经在 `beforeCreate` 之后调用。 |
| `created`       | 不需要（setup 已经是 created 之后调用）      | 组合式 API 中没有对应的钩子函数，因为 `setup` 函数已经在 `created` 之后调用。 |
| `beforeMount`   | `onBeforeMount`                              | 在挂载开始之前被调用，相关的 `render` 函数首次被调用。通常用于在初次渲染之前执行一些准备工作。 |
| `mounted`       | `onMounted`                                  | 挂载完成后调用，此时组件已经被渲染到 DOM。通常用于操作 DOM 或初始化与 DOM 相关的第三方库。 |
| `beforeUpdate`  | `onBeforeUpdate`                             | 数据变化导致的重新渲染之前调用。通常用于在组件更新之前执行一些任务。 |
| `updated`       | `onUpdated`                                  | 由于数据变化导致的虚拟 DOM 重新渲染和打补丁之后调用。通常用于在组件更新后执行一些任务。 |
| `beforeUnmount` | `onBeforeUnmount`                            | 组件实例卸载之前调用。通常用于在组件被移除之前执行一些清理工作。 |
| `unmounted`     | `onUnmounted`                                | 组件实例卸载之后调用。通常用于清理副作用（如定时器、事件监听等）。 |

# Vue3中setup()函数有什么用途？

在 Vue 3 中，`setup()` 函数是组合式 API 的核心部分，提供了一种新的方式来定义组件的逻辑。它在组件实例创建期间的非常早期阶段调用，是在 `beforeCreate` 和 `created` 生命周期钩子之前执行的。`setup()` 函数的主要用途包括：

### 1. 定义响应式状态

在 `setup()` 函数中，可以使用 Vue 提供的响应式 API（如 `ref` 和 `reactive`）来定义响应式状态。`ref` 用于创建单个值的响应式引用，`reactive` 用于创建对象的响应式引用。

### 2. 使用计算属性

可以在 `setup()` 函数中定义计算属性，使用 `computed` 函数来实现。

### 3. 声明方法

可以在 `setup()` 函数中定义方法，作为普通的 JavaScript 函数来声明，并在返回对象中公开这些方法。

### 4. 使用生命周期钩子

在 `setup()` 函数中，可以使用 Vue 提供的生命周期钩子函数来处理组件生命周期事件。

### 5. 使用依赖注入和提供

在 `setup()` 函数中，可以使用 `provide` 和 `inject` API 来实现依赖注入。

```javascript
import { provide, inject, ref } from 'vue';
```

### 6. 组合逻辑

通过 `setup()` 函数，可以将逻辑组织成可复用的函数，这些函数可以在多个组件中共享。这种方法被称为“组合函数”（Composition Functions）。

### 总结

`setup()` 函数在 Vue 3 中具有以下主要用途：

- 定义响应式状态（使用 `ref` 和 `reactive`）
- 使用计算属性（使用 `computed`）
- 声明方法
- 使用生命周期钩子（如 `onMounted`、`onUnmounted`）
- 使用依赖注入和提供（`provide` 和 `inject`）
- 组合逻辑（创建可复用的组合函数）

通过 `setup()` 函数，开发者可以更灵活地组织和复用逻辑，增强代码的可读性和维护性。

# Router和route的区别

### 1. Router

`router` 是 Vue Router 的实例，它管理应用程序的所有路由。Vue Router 提供了用于导航和配置路由的 API。通过 `router`，可以定义路由、导航到不同的路由以及访问全局路由状态。

#### 主要用途

- **定义路由**：使用 `routes` 配置定义应用程序的所有路由。
- **导航**：通过编程式导航或使用 `<router-link>` 组件在路由之间导航。
- **访问全局状态**：可以访问和修改全局路由状态，比如当前路由信息、导航守卫等。

### 2. Route

`route` 是当前激活的路由信息对象，它包含了与当前路由相关的所有信息，如路径参数、查询参数、路由名称等。`route` 对象是由 `router` 管理的，可以在组件中通过 `this.$route` 访问。

#### 主要用途

- **获取当前路由信息**：访问当前路由的路径、参数、查询参数、名称等。
- **动态路由匹配**：获取动态路径参数和查询参数。
- **访问路由元数据**：可以访问与当前路由相关的元数据。

#### 示例

在组件中访问 `route` 信息：

```vue
this.$route.path;
this.$route.query;
this.$route.params;  
```

### 总结

| 特点     | `router`                                 | `route`                                              |
| -------- | ---------------------------------------- | ---------------------------------------------------- |
| 定义     | Vue Router 实例，管理应用程序的所有路由  | 当前激活的路由信息对象                               |
| 主要用途 | 定义路由、导航、访问和修改全局路由状态   | 获取当前路由的信息，如路径、参数、查询参数、名称等   |
| 访问方式 | 通过 `this.$router` 或导入 `router` 实例 | 通过 `this.$route` 或组合式 API 中的 `useRoute` 获取 |
| 示例     | `this.$router.push('/about')`            | `this.$route.path`                                   |

### 总结

- **`router`**：Vue Router 实例，用于管理路由、导航和全局路由状态。
- **`route`**：当前激活的路由信息对象，用于获取当前路由的路径、参数、查询参数等。

# 组件之间通信的方式都有哪些

在 Vue.js 中，组件之间的通信是非常重要的，尤其是当应用程序变得复杂时。Vue 提供了多种方式来实现组件之间的通信，每种方式适用于不同的场景。下面列出了主要的组件通信方式，并解释了每种方式的用途和示例。

### 1. 父组件与子组件通信

#### Props

父组件可以通过 `props` 向子组件传递数据。`props` 是单向数据流，即数据从父组件流向子组件。

### 2. 子组件与父组件通信

#### Emit Events

子组件可以通过 `$emit` 触发事件，父组件通过监听这些事件来接收数据或执行操作。

### 3. 爷孙组件通信

#### Provide/Inject

`provide` 和 `inject` 用于在祖先组件和后代组件之间传递数据，适用于需要在组件树的深层次中共享数据的场景。

```vue
<!-- GrandparentComponent.vue -->
<template>
  <ParentComponent />
</template>

<script>
import ParentComponent from './ParentComponent.vue';
import { provide } from 'vue';

export default {
  components: { ParentComponent },
  setup() {
    provide('sharedData', 'Data from Grandparent');
  }
};
</script>
```



### 4. 跨级组件通信

#### Event Bus

Event Bus 是一个中央事件总线，通过它可以在任意组件之间传递事件。通常使用 Vue 实例或其他事件库来实现。

```javascript
// eventBus.js
import { createApp } from 'vue';
const eventBus = createApp({});
export default eventBus;
```

```vue
<!-- ComponentA.vue -->
<template>
  <button @click="sendMessage">Send Message</button>
</template>

<script>
import eventBus from './eventBus';

export default {
  methods: {
    sendMessage() {
      eventBus.$emit('message', 'Hello from Component A');
    }
  }
};
</script>
```

```vue
<!-- ComponentB.vue -->
<template>
  <p>{{ message }}</p>
</template>

<script>
import eventBus from './eventBus';

export default {
  data() {
    return {
      message: ''
    };
  },
  created() {
    eventBus.$on('message', (msg) => {
      this.message = msg;
    });
  }
};
</script>
```

### 5. 全局状态管理

Vuex 是一个专门为 Vue2.js 应用程序开发的状态管理模式。它通过集中式存储管理应用程序的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。

pinia3是一个用于 Vue3.js 应用程序的状态管理库（管理和共享状态（数据））。

### 6. 使用 Slots

通过插槽（Slots），父组件可以向子组件传递模板内容。插槽允许父组件将部分模板传递给子组件进行渲染。

### 总结

- **Props**: 父组件向子组件传递数据。
- **Emit Events**: 子组件向父组件传递数据或事件。
- **Provide/Inject**: 在祖先组件和后代组件之间传递数据。
- **Event Bus**: 在任意组件之间传递事件。
- **Vuex（v2）/pinia(v3)**: 全局状态管理，适用于大型应用。
- **Slots**: 父组件向子组件传递模板内容。

合理选择组件通信方式，可以提高代码的可维护性和可读性，适应不同的应用场景。

# 定义2个组件，登录和注册，通过路由的形式实现2个组件之间的切换

### 1. 安装 Vue Router(v3)

如果你还没有安装 Vue Router，可以通过以下命令安装：

```bash
npm install vue-router@4
```

### 2. 创建组件

首先，创建 `Login` 和 `Register` 组件。

### 3. 配置路由

创建或修改 `router/index.js`（或 `router.js`）文件来配置路由。

### 4. 在主应用中使用路由

在 `main.js` 文件中引入路由，并将其传递给 Vue 应用。

### 5. 创建主应用布局

在 `App.vue` 文件中，添加 `<router-view>` 标签以显示路由匹配的组件。

### 总结

- **定义组件**: 创建 `Login` 和 `Register` 组件，提供相应的表单和导航链接。
- **配置路由**: 使用 Vue Router 配置路由，将 `/login` 和 `/register` 路径与对应的组件关联。
- **使用路由**: 在主应用中引入并使用 Vue Router，将 `<router-view>` 标签放在 `App.vue` 中，以显示路由组件。

这样，你就实现了通过路由切换 `登录` 和 `注册` 组件的功能。

# pinia定义，有哪些核心以及核心理解

Pinia 是 Vue 3 官方推荐的状态管理库，它是 Vuex 的替代方案，提供了更加现代和简洁的 API。Pinia 旨在为 Vue 应用提供集中式的状态管理，并解决了一些 Vuex 中存在的问题。以下是 Pinia 的核心概念和理解：

### 1. **核心概念**

#### 1.1 Store（仓库）

- **定义**：在 Pinia 中，`store` 是一个用来存储应用状态和方法的对象。每个 `store` 是一个模块，负责管理相关状态和逻辑。
- **创建**：使用 `defineStore` 函数来定义一个 `store`。每个 `store` 都有一个唯一的 ID 和一个包含状态、getter 和 action 的配置对象。


#### 1.2 State（状态）

- **定义**：`state` 是 `store` 中的数据源，存储应用的状态。它是响应式的，任何对 `state` 的修改都会自动更新相关的组件。
- **使用**：可以在组件中通过 `useStore()` 获取 `store`，并访问和修改 `state`。

#### 1.3 Getters（计算属性）

- **定义**：`getters` 是 `store` 中的计算属性，用于计算基于 `state` 的派生状态。它们是只读的，类似于 Vue 的计算属性。
- **使用**：通过 `getters` 可以获取计算后的值，而不需要在组件中重复计算逻辑。

#### 1.4 Actions（方法）

- **定义**：`actions` 是 `store` 中的方法，用于处理异步操作或复杂逻辑。`actions` 可以修改 `state` 并调用其他 `actions`。
- **使用**：可以在 `actions` 中定义业务逻辑，并在组件中调用这些方法来改变 `state` 或执行其他操作。

#### 1.5 Modules（模块）

- **定义**：`store` 可以被组织成模块，每个模块有自己的 `state`、`getters` 和 `actions`，并且可以互相嵌套和组合。
- **使用**：将 `store` 拆分成多个模块可以提高代码的可维护性和可读性。

### 2. **核心理解**

#### 2.1 响应式

Pinia 的 `state` 是响应式的，使用了 Vue 3 的响应式系统，确保状态的变化能够立即反映到组件中。

#### 2.2 类型安全

Pinia 提供了 TypeScript 支持，允许在定义 `store` 时使用类型安全的方式。这有助于避免运行时错误，并提供更好的开发体验。

#### 2.3 轻量和高效

Pinia 比 Vuex 更加轻量和高效，简化了 API 和配置，避免了 Vuex 中的一些繁琐的 boilerplate 代码。

#### 2.4 模块化

Pinia 支持模块化的设计，使得可以将 `store` 拆分成多个模块，每个模块管理自己的状态和逻辑，从而提高代码的可维护性和组织性。

#### 2.5 支持 Vue Devtools

Pinia 与 Vue Devtools 兼容，允许开发者方便地查看和调试 `store` 的状态和变更。



