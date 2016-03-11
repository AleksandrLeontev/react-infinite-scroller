React Infinite Scroller
=======================

Infinitely load content using a React Component. This fork maintains a simple, lightweight infinite scroll package that supports both `window` and scrollable elements.

## Version

0.2.0 for React 14.7

## Installation

```
  npm i react-infinite-scroller
```

## How to use

Only supports ES6 import. For other versions, please see the many forks of the [original repository](https://github.com/guillaumervls/react-infinite-scroll)

```
  import InfiniteScroll from 'react-infinite-scroller'
```

### Window scroll events

```html
  <InfiniteScroll
      pageStart=0
      loadMore={loadFunc}
      hasMore={true || false}
      loader={<div className="loader">Loading ...</div>}>
    {items} // <-- This is the content you want to load
  </InfiniteScroll>
```

### DOM scroll events

```
  <div style="height:700px;overflow:auto;">
    <InfiniteScroll
        pageStart=0
        loadMore={loadFunc}
        hasMore={true || false}
        loader={<div className="loader">Loading ...</div>}
        useWindow={false}>
      {items}
    </InfiniteScroll>
  </div>
```

- `pageStart` : The page number corresponding to the initial `items`, defaults to `0`
                which means that for the first loading, `loadMore` will be called with `1`

- `loadMore(pageToLoad)` : This function is called when the user scrolls down
                           and we need to load items

- `hasMore` : Boolean stating whether there are more items to be loaded. Event listeners
              are removed if `false`.

- `loader` : Loader element to be displayed while loading items - You can use
             `InfiniteScroll.setDefaultLoader(loader);` to set a defaut loader
             for all your `InfiniteScroll` components

- `threshold` : The distance between the bottom of the page and the bottom of the
                window's viewport that triggers the loading of new items -
                *Defaults to `250`*

- `useWindow` : Boolean stating whether to add listeners to the window, or else, the DOMNode