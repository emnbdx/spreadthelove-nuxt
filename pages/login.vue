<template>
    <section class="section">
        <div class="container">
            <div class="col-4 offset-4">
                <h2 class="text-center">Welcome back!</h2>

                <Notification :message="error" v-if="error" />

                <form method="post" @submit.prevent="login">
                    <div class="mb-3">
                        <label class="form-label">Email</label>
                        <input type="email" class="form-control" name="email" v-model="email" />
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Password</label>
                        <input type="password" class="form-control" name="password" v-model="password" />
                    </div>
                    <button type="submit" class="btn btn-primary">Log In</button>
                </form>
                <div class="text-center" style="margin-top: 20px">
                    <p>
                        Don't have an account? <nuxt-link to="/register">Register</nuxt-link>
                    </p>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import Notification from '~/components/Notification'

export default {
    components: {
        Notification,
    },

    data() {
        return {
            email: '',
            password: '',
            error: null
        }
    },

    methods: {
        async login() {
            try {
                await this.$auth.loginWith('local', {
                    data: {
                        email: this.email,
                        password: this.password
                    }
                })

                this.$router.push('/')
            } catch (e) {
                this.error = e.response.data.message
            }
        }
    }
}
</script>