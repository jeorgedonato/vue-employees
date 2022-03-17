<template lang="">
    <div class="employees-table">
        <h4>List of Employees</h4>
        <table class="table">
            <thead>
                <tr>
                    <th>First Name</th>
                    <th>Last Name</th>
                    <th>Position</th>
                    <th>Start Date</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody >
                <EmployeeData  v-for="(employee, idx) in employees" v-bind:key="idx" :employee=employee :idx=idx @employee-deleted="handleDeleted" />

            </tbody>
        </table>
        <EmployeeForm @added-employee="handleAdded" @reset-employees="handleReset" />
    </div>  
</template>
<script>
import EmployeeData from './EmployeeData.vue'
import EmployeeForm from './EmployeeForm.vue'

const initialEmployees = () => {
    return {
        employees: [
                {
                    firstname: "Jeorge",
                    lastname: "Donato",
                    position: "Software Engineer",
                    start_date: "03/25/2019"
                },
                {
                    firstname: "John",
                    lastname: "Doe",
                    position: "Senior Software Engineer",
                    start_date: "08/25/2020"
                },
                {
                    firstname: "Lisa",
                    lastname: "Kudrow",
                    position: "Web Developer",
                    start_date: "10/02/2015"
                },
            ]
    }
}

export default {
    name: 'EmployeesTable',
    components: {
        EmployeeData,
        EmployeeForm
    },
    data(){
        return initialEmployees()
    },
    methods: {
        handleAdded: function(emp) {
            this.employees.push(emp)
        },
        handleDeleted: function (idx) {
            this.employees = this.employees.filter((emp, i) => i !== idx)
        },
        handleReset: function(){
            Object.assign(this.$data, initialEmployees())
        }
    }
}
</script>
<style >
    .table{
        margin-right: auto;
        margin-left: auto;
    }
</style>