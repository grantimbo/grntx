<script>

export let projects;
export let slug;
$: post = projects.find(p => p.slug == slug);

console.log(slug)

</script>

<div class="post">
  <h1>{ slug }</h1>
  <div class="post-content">{@html post.content }</div>
</div>