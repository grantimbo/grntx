<script>
import NavLink from './Navlink.svelte';
</script>

<nav class="project-cat">
    <NavLink to="projects"><i class="icon-all"></i> <span>All</span></NavLink>
    <NavLink to="project-type/concept-art"><i class="icon-image"></i> <span>Concept Arts</span></NavLink>
    <NavLink to="project-type/graphic-designs"><i class="icon-pen"></i> <span>Graphics & Design</span></NavLink>
    <NavLink to="project-type/product-renders"><i class="icon-glass"></i> <span>Product Renders</span></NavLink>
    <NavLink to="project-type/websites"><i class="icon-code"></i> <span>Websites</span></NavLink>
    <NavLink to="project-type/animations"><i class="icon-film"></i> <span>Animations</span></NavLink>
    <NavLink to="project-type/abstract-art"><i class="icon-quill"></i> <span>Abstract 3D</span></NavLink>
</nav>