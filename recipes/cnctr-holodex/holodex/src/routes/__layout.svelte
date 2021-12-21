<script>
    import Topnav from '../components/topnav.svelte';
    import Bottomnav from '../components/bottomnav.svelte';
</script>
<Topnav/>
<slot></slot>
<Bottomnav/>
<style>
@tailwind base;
@tailwind components;
@tailwind utilities;
</style>