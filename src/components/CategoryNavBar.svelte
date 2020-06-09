<script>
import NavLink from './Navlink.svelte';
</script>

<nav class="project-cat">
    <NavLink to="projects"><i class="icon-all"></i> <span>All</span></NavLink>
    <NavLink to="project-type/featured"><i class="icon-others"></i> <span>Featured</span></NavLink>
    <NavLink to="project-type/typography"><i class="icon-coffee"></i> <span>Typograhpy</span></NavLink>
    <NavLink to="project-type/motion"><i class="icon-motion"></i> <span>Motion</span></NavLink>
    <NavLink to="project-type/websites"><i class="icon-webdev"></i> <span>Websites</span></NavLink>
    <NavLink to="project-type/cars"><i class="icon-webdev"></i> <span>Cars</span></NavLink>
</nav>