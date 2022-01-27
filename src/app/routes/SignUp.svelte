<script>

    import users from "../logins";

    $: errorMessageUsername = username === "bad" ? "❌ username is bad" : "";
    $: errorMessagePassword = password === "bad" ? "❌ password is bad" : "";

    let username = "";
    let password = "";

    let serverErrorMessage = "";

    function signIn() {
        if (!users.addUser(username, password)) {
            serverErrorMessage = "Username already in use. Choose another one";
        } else {
            serverErrorMessage = "yay";
        }
    }

</script>

<div class="cards" style="width: 300px; margin: 0px auto;">
    <div class="card">
        <h5 class="card-header">Sign Up</h5>
        <div class="card-body" style="width: 275px">
            <input id="username-field" type="text" placeholder="Username" bind:value={username}/>
            <label for="username-field">{errorMessageUsername}</label>

            <input id="password-field" type="text" placeholder="Password" bind:value={password}/>
            <label for="password-field">{errorMessagePassword}</label>
        </div>
        <div class="card-footer right">
            <button on:click={signIn}>Sign Up</button>
        </div>
    </div>
</div>
