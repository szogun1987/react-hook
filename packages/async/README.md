<hr>
<div align="center">
  <h1 align="center">
    useAsync()
  </h1>
</div>

<p align="center">
  <a href="https://bundlephobia.com/result?p=@react-hook/async">
    <img alt="Bundlephobia" src="https://img.shields.io/bundlephobia/minzip/@react-hook/async?style=for-the-badge&labelColor=24292e">
  </a>
  <a aria-label="Types" href="https://www.npmjs.com/package/@react-hook/async">
    <img alt="Types" src="https://img.shields.io/npm/types/@react-hook/async?style=for-the-badge&labelColor=24292e">
  </a>
  <!--
  <a aria-label="Code coverage report" href="https://codecov.io/gh/jaredLunde/react-hook">
    <img alt="Code coverage" src="https://img.shields.io/codecov/c/gh/jaredLunde/react-hook?style=for-the-badge&labelColor=24292e">
  </a>
  <a aria-label="Build status" href="https://travis-ci.com/jaredLunde/react-hook">
    <img alt="Build status" src="https://img.shields.io/travis/com/jaredLunde/react-hook?style=for-the-badge&labelColor=24292e">
  </a>
  -->
  <a aria-label="NPM version" href="https://www.npmjs.com/package/@react-hook/async">
    <img alt="NPM Version" src="https://img.shields.io/npm/v/@react-hook/async?style=for-the-badge&labelColor=24292e">
  </a>
  <a aria-label="License" href="https://jaredlunde.mit-license.org/">
    <img alt="MIT License" src="https://img.shields.io/npm/l/@react-hook/async?style=for-the-badge&labelColor=24292e">
  </a>
</p>

<pre align="center">npm i @react-hook/async</pre>
<hr>

A React hook for gracefully resolving and cancelling async functions and promises

## Quick Start

```jsx harmony
import {useAsync, useAsyncEffect} from '@react-hook/async'

// Example using a manual invocation
const CallbackResolver = () => {
  const [{status, cancel, error, value}, call] = useAsync(() => {
    new Promise((resolve) => setTimeout(() => resolve('Loaded'), 1000))
  }, [])

  switch (status) {
    case 'loading':
      return (
        <React.Fragment>
          <button onClick={cancel}>Cancel</button>
          Loadng...
        </React.Fragment>
      )
    case 'error':
      return `Error: ${error}`
    case 'success':
      return value
    case 'idle':
      return <button onClick={call}>Load me</button>
  }
}

// Example using a useEffect invocation
const EffectResolver = () => {
  const [curr, setCurr] = useState(0)
  // Will load each time counter changes
  const {status, cancel, error, value} = useAsyncEffect(() => {
    new Promise((resolve) => setTimeout(() => resolve(`Loaded ${curr}`), 1000))
  }, [curr])

  switch (status) {
    case 'loading':
      return (
        <React.Fragment>
          <button onClick={cancel}>Cancel</button>
          Loadng...
        </React.Fragment>
      )
    case 'error':
      return `Error: ${error}`
    case 'success':
      return (
        <React.Fragment>
          {value}
          <button onClick={() => setCurr((curr) => ++curr)}>Load again</button>
        </React.Fragment>
      )
    case 'idle':
      return <button onClick={call}>Load me</button>
  }
}
```

## API

### Props

| Prop | Type | Default | Required? | Description |
| ---- | ---- | ------- | --------- | ----------- |
|      |      |         |           |             |

## LICENSE

MIT