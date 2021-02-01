<template>
    <div>
        <form @submit.prevent="submit" class="m-3">

            <div class="form-group">
                <label for="name">Name</label>
                <input
                    type="text"
                    v-model="form.name"
                    class="form-control"
                    id="name"
                    placeholder="Name"
                />
            </div>

            <div class="form-group">
                <label for="email">Email</label>
                <input
                    type="email"
                    v-model="form.email"
                    class="form-control"
                    id="email"
                    placeholder="Email"
                    :class="{ 'is-invalid': errors.email }"
                />
                <div class="invalid-feedback">
                    {{ errors.email }}
                </div>
            </div>
            <div class="form-group">
                <label for="password">Password</label>
                <input
                    type="password"
                    v-model="form.password"
                    class="form-control"
                    id="password"
                    placeholder="Password"
                />
            </div>
            <button
                type="submit"
                class="btn btn-outline-primary mt-2 btn-sm float-right"
            >
                Update
            </button>
            <inertia-link
                href="/user"
                class="btn btn-outline-secondary btn-sm mt-2"
            >
                Cancel
            </inertia-link>
        </form>
    </div>
</template>

<script>
export default {
    props: ["user", "errors"],
    data() {
        return {
            form: {
                name: this.user.name,
                email: this.user.email,
                password: ""
            }
        };
    },
    methods: {
        submit() {
            this.$emit("submit", this.form);
        }
    }
};
</script>

<style lang="scss" scoped></style>
