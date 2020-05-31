<script>
  import {isActive, url} from '@sveltech/routify'

  const links =
  [
    ['/', 'Home'],
    ['/projects', 'Projects'],
    ['/about', 'About'],
    ['/services', 'Services']
  ]
</script>

<style>
  .active {font-weight: bold}
</style>

<ul>
  {#each links as [path, name]}
    <!-- Svelte magic. If isActive is true, the "active" class is applied. -->
    <li class:active={$isActive(path)}>
      <a href={$url(path)}>
        {name}
      </a>
    </li>
  {/each}
</ul>