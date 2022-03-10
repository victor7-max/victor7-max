<script setup>
    import BreezeButton from "@/Components/Button.vue";
    import BreezeGuestLayout from "@/Layouts/Guest.vue";
    import BreezeInput from "@/Components/Input.vue";
    import BreezeLabel from "@/Components/Label.vue";
    import BreezeValidationErrors from "@/Components/ValidationErrors.vue";
    import {
        Head,
        Link,
        useForm
    } from "@inertiajs/inertia-vue3";

    const form = useForm({
        name: "",
        username: "",
        gender: "male",
        email: "",
        password: "",
        password_confirmation: "",
        terms: false
    });

    const submit = () => {

        form.post(route("register"), {
            onFinish: () => form.reset("password", "password_confirmation")
        });
    };

</script>

<template>
    <div>

        <Head title="Register" />

        <BreezeValidationErrors class="mb-4" />

        <form @submit.prevent="submit">
            <div class="form-group">
                <input type="text" v-model="form.name" required="required" />
                <label class="control-label" for="input">First & Last Name</label>
                <i class="mtrl-select"></i>
            </div>
            <div class="form-group">
                <input type="text" v-model="form.username" required="required" />
                <label class="control-label" for="input">User Name</label>
                <i class="mtrl-select"></i>
            </div>
            <div class="form-group">
                <input type="text" v-model="form.email" required="required" />
                <label class="control-label" for="input">Email</label>
                <i class="mtrl-select"></i>
            </div>
            <div class="form-group">
                <input type="password" v-model="form.password" required="required" />
                <label class="control-label" for="input">Password</label>
                <i class="mtrl-select"></i>
            </div>
            <div class="form-group">
                <input type="password" v-model="form.password_confirmation" required="required" />
                <label class="control-label" for="input">Confirm Password</label>
                <i class="mtrl-select"></i>
            </div>

            <div class="form-group">
                <select v-model="form.gender" class="form-control">
                    <option value="male">Male here</option>
                    <option value="female">Female</option>
                </select>
            </div>

            <div class="checkbox">
                <label>
                    <input type="checkbox" checked="checked" />
                    <i class="check-box"></i>Accept Terms & Conditions ?
                </label>
            </div>
            <a href="#" title class="already-have">Already have an account</a>
            <div class="submit-btns">
                <button class="mtr-btn ">
                    <span>Register</span>
                </button>
            </div>
        </form>
    </div>
</template>
