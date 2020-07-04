<script>
  import { Link } from "svelte-routing";

  export let to = "";

  function getProps({ location, href, isPartiallyCurrent, isCurrent }) {
    const isActive = href === "/" ? isCurrent : isPartiallyCurrent || isCurrent;

    // The object returned here is spread on the anchor element's attributes
    if (isActive) {

      // if page is /projects/* toggle 'hideOverflow' body class
      let projectLink = location.pathname.includes('/projects/');

      if (projectLink) {
        document.querySelector('body').classList.add('hideOverflow');
      } else {
        document.querySelector('body').classList.remove('hideOverflow');
      }

      return { class: "active" };
    }
    return {};
  }
</script>

<Link to="{to}" getProps="{getProps}">
  <slot />
</Link>