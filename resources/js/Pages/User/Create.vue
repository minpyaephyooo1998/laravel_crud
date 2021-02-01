<template>
    <div class="container my-5">
        <div class="row justify-content-center">
            <div class="col-8">
                <div class="card">
                    <h2 class="m-2">Create User</h2>
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
    name: "Create",
    props: ["user", "errors"],

    methods: {
        submit(form) {
            this.$inertia.post("/user", form);
        }
    }
};
</script>

<style lang="scss" scoped></style>
