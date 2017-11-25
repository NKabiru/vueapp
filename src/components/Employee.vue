<script>
var mixin = {
    methods: {
        addEmployee(){
            this.employee.id  =`EK${this.employeeList.length + 1}`;
            this.employeeList.push(this.employee);
            this.employee = {};
        }
    }
    };
export default {
    name: 'Employee',
    data() {
        return {
            employee: {},
            formtitle: 'Form',
            tabletitle: 'Employee Table',
            employeeList: [],
            tableClass: 'unstriped',
        }    
    },
    mixins: [mixin],
    computed:{
        updateTitle(){
            return 'Employees ' + this.formtitle;
        }
    },
    methods: {
        employeeNumber(){
            console.log(this.employeeList.length);
        },
        added(){
            console.log('New employee added');
            this.$emit('added');
        },
        netIncome(income){
            return Math.round(income * 85) / 100;
        }
    }
}
</script>

<template>
    <div>
        <h4>{{ updateTitle }}</h4>
        <div class="grid-x grid-margin-x align-center">
            <div class="large-auto cell">
                First Name<input type="text" v-model="employee.fname">
                Last Name<input type="text" v-model="employee.lname">
                Job<select v-model="employee.job">
                <option value="Developer">Developer</option>
                <option value="Operator">Operator</option>
                <option value="Manager">Manager</option>
                <option value="Technician">Technician</option>
                <option value="Advisor">Advisor</option>
            </select>
                Income<input type="number" v-model="employee.income">
                <button class="button" type="button" @click="addEmployee" :added="employeeNumber">Add</button>
            </div>
        </div>
        <template v-if="employeeList.length >= 1">
        <div class="grid-x grid-margin-x align-center">
            
            <div class="cell">
                <h4>{{ tabletitle }}</h4>
                <table v-bind:class="tableClass">
                    <thead>
                        <tr>
                            <td>ID</td>
                            <td>Name</td>
                            <td>Occupation</td>
                            <td>Gross Income</td>
                            <td>Net Income</td>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="employee in employeeList" v-bind:key='employee.id'>
                            <td>{{ employee.id }}</td>
                            <td>{{ employee.fname }} {{ employee.lname}}</td>
                            <td>{{ employee.job }}</td>
                            <td>{{ employee.income}}</td>
                            <td>{{ netIncome(employee.income) }}</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

        </template>
  </div>

</template>



<style>

</style>


