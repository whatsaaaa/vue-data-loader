<h1 align="center">vue-data-loader - Vue 3 component for enhancing the UX while data is being fetched from the backend</h1>

<p align="center">
  <sub>Made by <a href="https://github.com/whatsaaaa">@whatsaaaa</a>
</p>

## Installation

```sh
npm install @whatsaaaaa/vue-data-loader-component --save
```

## Usage

With `vue-data-loader-component` you can fetch the data from any backend. It is built on top of [VueDataFetch](https://github.com/whatsaaaa/VueDataFetch) module. If you want to understand how this component works behind the scenes, take a look at that repository as well.

### Basic Example

```javascript
import DataLoader from "@whatsaaaaa/vue-data-loader-component";
...

<DataLoader url="https://jsonplaceholder.typicode.com/posts" />
```

This is very basic example and it should be used only as a starting point. From it we can see that `DataLoader` component has one (required) prop called `url`.

If you run this example in your application you won't see anything special, it will just display if your request was successful or not. Please take a look at `real-world example` for proper usage.

### Real-world Example

```javascript
import DataLoader from "@whatsaaaaa/vue-data-loader-component";

<DataLoader url="https://jsonplaceholder.typicode.com/posts/1">
  <template #loader>
    ...
  </template>
  <template #data="{ data }">
    ...
  </template>
  <template #error="{ error }">
    ...
  </template>
</DataLoader>;
```

In this example we can see all the `features` of `DataLoader` component, and this is how it is supposed to be used.

As we can see `DataLoader` component offers us three `slots`:

- `loader`: Content of this slot will be visible while we are waiting for the response from the backend.
- `data`: Content of this slot will be visible if our request was successful. Response data will be available in the `data` slot prop.
- `error`: Content of this slot will be visible if our request failed. Error data will be available in the `error` slot prop. Error object will always contain three properties: `status`, `statusText` & `response`.

```javascript
import DataLoader from "@whatsaaaaa/vue-data-loader-component";

<DataLoader url="https://jsonplaceholder.typicode.com/posts/1">
  <template #loader>
    <LoadingSpinner />
  </template>
  <template #data="{ data }">
    <PostItem :post="data" />
  </template>
  <template #error="{ error }">
    Oh no, your request failed with the status code: {{ error.status }}
   </template>
</DataLoader>;
```

## Dependencies

- `Vue`: ^3.0.2
- `@whatsaaaaa/vue-data-fetch`: ^0.1.1
