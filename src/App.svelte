<script lang="ts">
  export let name: string;
  let stringTest = `this string contains some <strong>HTML!!!</strong>`;
  import Info from './Info.svelte';
  import Nested from './Nested.svelte';
  // 引用传值 es6 ...
  const pkg = {
    name: 'kk德米安',
    version: 3,
    speed: '吧啦吧啦',
    website: 'https://dfinity.dev'
  };

  // count
  let count = 0;
  // 反应式声明
  $: doubled = count * 2;

  $: if (count >= 18) {
    alert(`count is dangerously high!`);
    count = 17;
  }

  function handleClick() {
    count += 1;
  }

  // 赋值
  let numbers = [1, 2, 3, 4];

  function addNumber() {
    numbers = [...numbers, numbers.length + 1];
  }

  $: sum = numbers.reduce((t, n) => t + n, 0);
</script>

<main>
  <h1>Hello {name}!</h1>
  <p>
    Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
    how to build Svelte apps.
  </p>
  <p>{@html stringTest}</p>

  <p>props:</p>
  <Nested tnested={444} />

  <button on:click={handleClick}>
    Clicked {count}
    {count === 1 ? 'time' : 'times'}
  </button>

  <p>{count} doubled is {doubled}</p>

  <p>{numbers.join(' + ')} = {sum}</p>

  <button on:click={addNumber}> Add a number </button>
  <p>引用传值:</p>
  <Info {...pkg} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
