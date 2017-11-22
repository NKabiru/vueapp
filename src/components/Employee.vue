<script>
export default {
    name: 'Employee',
    data() {
        return {
            formtitle: 'Employee Form',
            tabletitle: 'Employee Table',
            employeeList: [],
            tableClass: 'unstriped',
            id: 0,
            fname: '',
            lname: '',
            job: '',
            income: 0
        }    
    },
    methods: {
        addEmployee: function(){
            this.employeeList.push({
                id: this.id++,
                fname: this.fname,
                lname: this.lname,
                job: this.job,
                income: this.income
            });

                this.fname  = '';
                this.lname = '';
                this.job = '';
                this.income = '';
        }
    }
}
</script>

<template>
    <div class="grid-container">
        <h3>{{ formtitle }}</h3>
        <div class="grid-x grid-margin-x align-center">
            
            <div class="medium-6 cell">
                First Name<input type="text" v-model="fname">
                Last Name<input type="text" v-model="lname">
            </div>

            <div class="medium-6 cell">
            Job<select v-model="job">
                    <option value="Developer">Developer</option>
                    <option value="Operator">Operator</option>
                    <option value="Manager">Manager</option>
                    <option value="Technician">Technician</option>
                    <option value="Advisor">Advisor</option>
                </select>
                Income<input type="number" v-model="income">
            </div>
            
            <button class="button" type="button" @click="addEmployee">Add</button>
        </div>
        
        <div class="grid-x grid-margin-x">
            <h3>{{ tabletitle }}</h3>
            <div class="cell">
                <table v-bind:class="">
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
                            <td>{{ employee.income * 0.85 }}</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
  </div>

</template>



<style>

</style>


