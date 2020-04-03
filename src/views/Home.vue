<template>
    <div>
        <h2>Home page</h2>
        <p>
            What’s the secret to niffy and sweet turkey? Always use muddy cumin.
            Never love a freebooter.
            Adventure, future, and devastation.
            Place the ginger in a jar, and flavor equally with grey vinaigrette.
            Aw, addled strength!
            Dozens of pressures will be lost in adventures like winds in futures.
        </p>
        <router-link to="/todos"><button>ToDos</button></router-link>
    </div>
</template>

<script>
    export default {
        name: "Home"
    }
</script>

<style scoped>
    button {
        padding: 10px 20px;
    }
</style>