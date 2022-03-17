<template lang="">
    <div>
        <h5>Employee Form</h5>
        <form>
            <p> 
               First Name: <input v-model="formData.firstname" />
            </p>
            <p> 
               Last Name: <input v-model="formData.lastname" />
            </p>
            <p> 
               Position: <input v-model="formData.position" />
            </p>
            <p> 
               Start Date: <input v-model="formData.start_date" />
            </p>
            <button type="button" @click.prevent="addHandler">Add Button</button>
            <button style="margin-left: 10px;" type="button" @click.prevent="resetHandler">Reset Button</button>
        </form>
    </div>
</template>
<script>

const initialFormData = () => {
    return {
        formData: {
            firstname: '',
            lastname: '',
            position: '',
            start_date: ''
        }
    }
}
export default {
    name: 'EmployeeForm',
    data(){
        return initialFormData()
    },
    methods: {
        addHandler: function() {
            this.$emit("addedEmployee", this.formData)
            Object.assign(this.$data, initialFormData())
        },
        resetHandler() {
            this.$emit("resetEmployees")
        }
    }
}
</script>
<style lang="">
    
</style>