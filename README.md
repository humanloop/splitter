# Splitter

Splitter is a React component that allows you to split views into resizable panels. Similar to tabs in Visual Studio Code, for example. It's used in [Devbook](https://usedevbook.com) - A Search Engine for Developers.
Here's a gif of what you can build with Splitter:
![](example.gif)

Splitter is inspired by [Split.js](https://split.js.org/) and written as 100% functional component:

* All size calculation is done through CSS using `calc` with minimal JS. This makes it much faster

* Fully responsive

* No dependencies beside React

* Minimal assumptions about your styling and views

[CodeSandbox project](https://codesandbox.io/s/devbookhqspliiter-example-l23s4)

## Installing

### npm

```bash
npm install @devbookhq/splitter
```

### yarn

```bash
yarn add @devbookhq/splitter
```

## Usage

### Horizontal split

```tsx {"cell-id":"hejNBw","running-env-id":"877a4e26afd0","running-env-local-id":"zqnjCN","template-id":"nextjs-v11-components","cell-name":"Untitled-hls"}
import Splitter, { SplitDirection } from '@devbookhq/splitter'

function MyComponent() {
  return (
    <Splitter>
      <div className="tile">Tile 1</div>
      <div className="tile">Tile 2</div>
    </Splitter>
  );
}

export default MyComponent;
```

### Vertical split

```tsx {"cell-id":"PqY0M7","running-env-id":"877a4e26afd0","running-env-local-id":"zqnjCN","template-id":"nextjs-v11-components","cell-name":"Untitled-Xrr"}
import Splitter, { SplitDirection } from '@devbookhq/splitter'

function MyComponent() {
  return (
    <Splitter
      direction={SplitDirection.Vertical}  
    >
      <div className="tile">Tile 1</div>
      <div className="tile">Tile 2</div>
    </Splitter>
  );
}

export default MyComponent;
```

### Nested split

```tsx {"cell-id":"Wu9K0r","running-env-id":"877a4e26afd0","running-env-local-id":"zqnjCN","template-id":"nextjs-v11-components","cell-name":"Untitled-SxS"}
import Splitter, { SplitDirection } from '@devbookhq/splitter'

function MyComponent() {
  return (
    <Splitter direction={SplitDirection.Vertical}>
      <div className="tile">Tile 1</div>
      <Splitter direction={SplitDirection.Horizontal}>
        <div className="tile">Tile 2</div>
        <Splitter direction={SplitDirection.Vertical}>
          <div className="tile">Tile 3</div>
          <div className="tile">Tile 4</div>
        </Splitter>
      </Splitter>
    </Splitter>
  );
}

export default MyComponent;
```

### Get sizes of tiles

```tsx {"cell-id":"h2cYey","running-env-id":"877a4e26afd0","running-env-local-id":"zqnjCN","template-id":"nextjs-v11-components","cell-name":"Untitled-XF6"}
import Splitter, { SplitDirection } from '@devbookhq/splitter'

function MyComponent() {
  function handleResizeStarted(gutterIdx: number) {
    console.log('Resize started!', gutterIdx);
  }
  function handleResizeFinished(gutterIdx: number, newSizes: number[]) {
    console.log('Resize finished!', gutterIdx, newSizes);
  }

  return (
    <Splitter
      direction={SplitDirection.Vertical}
      onResizeStarted={handleResizeStarted}
      onResizeFinished={handleResizeFinished}
    >
      <div className="tile">Tile 1</div>
      <div className="tile">Tile 2</div>
    </Splitter>
  );
}

export default MyComponent;
```

To see more examples check out the [examples](#Example) section.

## Examples

Check the [`example`](./example/src/App.tsx) folder or the [CodeSandbox project](https://codesandbox.io/s/devbookhqspliiter-example-l23s4).

* [Horizontal](./example/src/HorizontalSplit/index.tsx)

* [Vertical](./example/src/VerticalSplit/index.tsx)

* [Nested](./example/src/NestedSplit/index.tsx)

* [Styled gutter](./example/src/StyledGutter/index.tsx)

* [Minimal tile size](./example/src/MinSize/index.tsx)

* [Initial tile sizes](./example/src/InitialSizes/index.tsx)

* [Scrollable tiles](./example/src/ScrollableChildren/index.tsx)

* [Get sizes of tiles](./example/src/OnDidResize/index.tsx)