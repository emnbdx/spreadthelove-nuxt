<template>
    <nav class="navbar navbar-expand-lg bg-light">
        <div class="container-fluid">
            <nuxt-link class="navbar-brand" to="/">Nuxt Auth</nuxt-link>

            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li class="nav-item dropdown" v-if="isAuthenticated">
                    <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown"
                        aria-expanded="false">
                        {{ loggedInUser.email }}
                    </a>
                    <ul class="dropdown-menu">
                        <li>
                            <nuxt-link class="navbar-item" to="/profile">My Profile</nuxt-link>
                        </li>
                        <li>
                            <hr class="dropdown-divider">
                        </li>
                        <li>
                            <a class="navbar-item">Logout</a>
                        </li>
                    </ul>
                </li>
                <template v-else>
                    <li class="nav-item">
                        <nuxt-link class="navbar-item" to="/register">Register</nuxt-link>
                    </li>&nbsp;
                    <li class="nav-item">
                        <nuxt-link class="navbar-item" to="/login">Log In</nuxt-link>
                    </li>
                </template>
            </ul>
        </div>
    </nav>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
    computed: {
        ...mapGetters(['isAuthenticated', 'loggedInUser'])
    }
}
</script>