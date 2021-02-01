<template>
    <div class="container">
        <div class="row mt-3">
            <div class="col-12">
                <h1>User List</h1>
                <p class="alert alert-info" v-show="success">
                    {{ success }}
                </p>

                <div class="row">
                    <div class="col-6">
                        <inertia-link
                            href="/user/create"
                            class="btn btn-success mb-3"
                            >Create</inertia-link
                        >
                    </div>
                </div>
                <table class="table">
                    <thead>
                        <tr>
                            <td>ID</td>
                            <td>Name</td>
                            <td>Email</td>
                            <td>date</td>
                            <td>Actions</td>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="user in users" :key="user.id">
                            <td>{{ user.id }}</td>
                            <td>{{ user.name }}</td>
                            <td>{{ user.email }}</td>
                            <td>{{ user.created_at }}</td>
                            <td>
                                <inertia-link
                                    :href="`/user/${user.id}/edit`"
                                    class="btn btn-success"
                                    >Edit</inertia-link
                                >
                                <button
                                    @click="destroy(user.id)"
                                    class="btn btn-danger"
                                >
                                    Delete
                                </button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Index",
    props: ["users", "success"],
    methods: {
        destroy(id) {
            this.$inertia.delete(`/user/${id}`);
        }
    }
};
</script>

<style lang="scss" scoped></style>
