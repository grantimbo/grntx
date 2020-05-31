<script>

    import { params } from '@sveltech/routify';

    export let slug;
    $: slug = $params.slug;

    console.log(slug)
</script>