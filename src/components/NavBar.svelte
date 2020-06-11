<script>
import NavLink from './Navlink.svelte';
</script>

<nav class="main">
    <NavLink to="/"><i class="material-icons">home</i><span>Home</span></NavLink>
    <NavLink to="projects"><i class="material-icons">photo_library</i><span>Projects</span></NavLink>
    <NavLink to="services"><i class="material-icons">style</i><span>Services</span></NavLink>
    <NavLink to="about"><i class="material-icons">account_circle</i><span>About</span></NavLink>
</nav>