<template>
    <div class="container my-5">
        <div class="row justify-content-center">
            <div class="col-8">
                <div class="card">
                    <h2 class="m-2">Edit User</h2>
                    <user-from :user="user" :errors="errors" @submit="submit" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import UserFrom from "./UserFrom.vue";

export default {
    components: { UserFrom },
    name: "Edit",
    props: ["user", "errors"],

    methods: {
        submit(form) {
            this.$inertia.put(`/user/${this.user.id}`, form);
        }
    }
};
</script>

<style lang="scss" scoped></style>
