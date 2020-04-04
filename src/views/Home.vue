<template>
    <div class="p-10">
        <h2 class="text-2xl text-blue-900 px-8 mb-6 font-bold">Home page</h2>
        <p class="text-blue-900 mb-6">
            What’s the secret to niffy and sweet turkey? Always use muddy cumin.
            Never love a freebooter.
            Adventure, future, and devastation.
            Place the ginger in a jar, and flavor equally with grey vinaigrette.
            Aw, addled strength!
            Dozens of pressures will be lost in adventures like winds in futures.
        </p>
        <router-link to="/todos" class="flex justify-end mr-6">
            <button class="bg-green-400 hover:bg-green-600 active:bg-green-900 text-white font-bold py-2 px-4
            rounded text-xl">
                To Application
            </button></router-link>
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