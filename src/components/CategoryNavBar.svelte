<script>
import NavLink from './Navlink.svelte';
</script>

<nav class="project-cat">
    <NavLink to="projects"><i class="material-icons">apps</i> <span>All</span></NavLink>
    <NavLink to="project-type/featured"><i class="material-icons">border_all</i> <span>Featured</span></NavLink>
    <NavLink to="project-type/typography"><i class="material-icons">font_download</i> <span>Typography</span></NavLink>
    <NavLink to="project-type/motion"><i class="material-icons">play_circle_filled</i> <span>Videos</span></NavLink>
    <NavLink to="project-type/websites"><i class="material-icons">code</i> <span>Websites</span></NavLink>
    <NavLink to="project-type/cars"><i class="material-icons">directions_car</i> <span>Cars Renders</span></NavLink>
</nav>