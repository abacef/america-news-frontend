<script>
    // export let name_from_prop;

    import {getGreeting} from "./api"

    import NavBar from "./NavBar.svelte"

    import Router from 'svelte-spa-router'

    import Home from "./routes/Home.svelte";
    import About from "./routes/About.svelte";
    import Blog from "./routes/Blog.svelte";
    import SignIn from "./routes/SignIn.svelte"
    import NotFound from "./routes/NotFound.svelte";
    import SignUp from "./routes/SignUp.svelte";

    const routes = {
        '/': Home,
        '/about': About,
        '/blog': Blog,
        '/sign-up': SignUp,
        '/sign-in': SignIn,
        '*': NotFound,
    }

</script>

<NavBar/>

<!-- Where the content of what is rendered for each route shows up -->
<Router {routes}/>

{#await getGreeting()}
    <p>...waiting for response from rocket</p>
{:then rocket_resp}
    <p>We are connected to the rocket server!: {rocket_resp}</p>
{:catch error}
    <p style="color: red">{error.message}</p>
{/await}


