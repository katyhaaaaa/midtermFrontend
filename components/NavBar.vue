<template>
    <div>
        <b-navbar toggleable="sm" type="light" variant="light">

            <b-navbar-brand href="/">Novel</b-navbar-brand>

            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

            <b-collapse id="nav-collapse" is-nav>
                
                <b-navbar-nav class="ml-auto">

                    <template v-if="$auth.loggedIn">
                        <b-nav-item href="/dashboard">Dashboard</b-nav-item>
                        <b-nav-item href="/novels">Novel</b-nav-item>
                        <b-nav-item href="#" @click.prevent="onLogout">Logout</b-nav-item>
                    </template>

                    <template v-else>
                        <b-nav-item href="/register">Register</b-nav-item>
                        <b-nav-item href="/login">Login</b-nav-item>
                    </template>

                </b-navbar-nav>

            </b-collapse>

        </b-navbar>
    </div>
</template>
<script>
export default {
    methods: {
        async onLogout() {
            this.$auth.logout()
        }
    }
}
</script>
