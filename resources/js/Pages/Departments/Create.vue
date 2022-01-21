<template>
    <breeze-authenticated-layout>
        <template #header>
            <breeze-heading>Create Departments</breeze-heading>
        </template>
                        <div v-show="form.hasErrors">
                            <div class="text-red-600 font-medium">Please make the following corrections:</div>
                        </div>
                        <form @submit.prevent="submit">
                            <div>
                                <breeze-label for="name" value="Name"></breeze-label>
                                <breeze-input type="text" id="name" class="mt-1 block w-1/2" v-model="form.name" required autofocus>

                                </breeze-input>
                                <breeze-input-error :message="form.errors.name"></breeze-input-error>
                            </div>
                            <div class="mt-4">
                                <breeze-label for="email" value="Email"></breeze-label>
                                <breeze-input type="email" id="email" class="mt-1 block w-1/2" v-model="form.email">

                                </breeze-input>
                                <breeze-input-error :message="form.errors.email"></breeze-input-error>
                            </div>
                            <div class="mt-4">
                                <breeze-label for="phone" value="Phone"></breeze-label>
                                <breeze-input type="text" id="phone" class="mt-1 block w-1/2" v-model="form.phone">

                                </breeze-input>
                                <breeze-input-error :message="form.errors.phone"></breeze-input-error>
                            </div>
                            <!-- submit -->
                            <div class="flex items-center justify-end mt-4">
                                <breeze-reset-button @click="resetForm">Reset</breeze-reset-button>
                                <breeze-button
                                :loading="form.processing">Create</breeze-button>
                            </div>
                        </form>
    </breeze-authenticated-layout>
</template>

<script>
import BreezeLink from "@/Components/AnchorLink"
import BreezeLabel from "@/Components/Label"
import BreezeInput from "@/Components/Input"
import BreezeInputError from "@/Components/InputError"
import BreezeButton from "@/Components/Button"
import BreezeResetButton from "@/Components/ResetButton"
import BreezeAuthenticatedLayout from '@/Layouts/Authenticated'
import { useForm } from '@inertiajs/inertia-vue3'


export default {
    components: {
        BreezeAuthenticatedLayout,
        BreezeLink,
        BreezeLabel,
        BreezeInput,
        BreezeResetButton,
        BreezeInputError,
        BreezeButton
    },
    setup(){
        const form = useForm({
            name:null,
            email:null,
            phone:null
        })

        return { form }
    },
    methods:{
        submit() {
            this.form.post(route('departments.store'));
        },
        resetForm() {
            this.form.clearErrors();
            this.form.reset();
        }
    }
}
</script>
