<template>
    <div>
        <div class="form-group">
            <label for="firstName">
                First Name:
            </label>
            <input
                    id="firstName"
                    type="text"
                    class="form-control"
                    :value="firstName"
                    @input="changeName($event)">
        </div>
        <div class="form-group">
            <label for="lastName">
                Last Name:
            </label>
            <input
                    id="lastName"
                    type="text"
                    class="form-control"
                    :value="lastName"
                    @input="changeName($event)">
        </div>
    </div>
</template>

<script>
    export default {
        name: "fullName",
        props: ['value'],
        computed: {
            firstName() {
                return this.value.split(' ')[0];
            },
            lastName() {
                return this.value.split(' ')[1];
            }
        },
        methods: {
            changeName(event) {
                const idField = event.target.id;
                let fullName = '';
                if(idField == 'firstName') {
                    fullName = event.target.value + ' ' + this.lastName;
                } else {
                    fullName = this.firstName + ' ' +  event.target.value;
                }
                this.$emit('input', fullName);
            }
        }
    }
</script>

<style scoped>

</style>