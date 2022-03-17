<template lang="">
    <tr>
        <td>{{employee.firstname}}</td>
        <td>{{employee.lastname}}</td>
        <td>{{employee.position}}</td>
        <td>{{employee.start_date}}</td>
        <td><button type="button" @click="handleDelete(idx)">Delete</button></td>
    </tr>
</template>
<script>
export default {
    name: 'EmployeeData',
    props: {
        'employee': Object,
        'idx': Number
    },
    methods: {
        handleDelete: function(idx) {
            this.$emit("employeeDeleted", idx)
        }
    }
}
</script>
<style lang="">
    
</style>