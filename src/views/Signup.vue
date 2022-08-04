<template>
    <div>
        <form @submit.prevent="handleSubmit">
            <label>Email: </label>
            <input type="email" v-model="email" required>
            <label>Password: </label>
            <input type="password" v-model="password" required>
            <div class="error">
                <p v-if="passwordError">{{ passwordError }}</p>
            </div>
            <label>Role:</label>
            <select v-model="role">
                <option value="web designer"> Web Designer </option>
                <option value="web Developer"> Web Developer </option>
            </select>
            <label for="">Skill</label>
            <input type="text" v-model="tempSkill" @keyup.ctrl="addSkill">
            <div v-for="skill in Skills" :key="skill" class="pills">
               <span @click="deleteSkill(skill)"> {{ skill }}</span>
            </div>
           <div class="term">
                <input type="checkbox" name="" value="yes" v-model="term">
                <label >Acept Term and Condition:</label>
           </div>
           <div class="submit">
                <button type="submit">Create an account</button>
           </div>
        </form>

        <p>Eamil: {{email}}</p>
        <p>Password: {{ password }}</p>
        <p>Role: {{ role }}</p>
        <p>term: {{ term }}</p>

    </div>
</template>

<script>
export default {
    name: 'VueProSignup',

    data() {
        return {
            email: '',
            password: '',
            role: '',
            term: false,
            tempSkill: '',
            Skills: [],
            passwordError :''
        };
    },

    mounted() {
      
    },

    methods: {
          addSkill(e){
            if (e.key === ',' && this.tempSkill) {
                if (!this.Skills.includes(this.tempSkill)) {
                    this.Skills.push(this.tempSkill)
                }
                
                this.tempSkill = ''
            }
            console.log(e)
        },
        deleteSkill(skill){
            this.Skills = this.Skills.filter((item) =>{
                console.log('before filter', this.Skills)
                return skill !== item
            })
            console.log('after filter', this.Skills)
        },
        handleSubmit(){
            this.passwordError = this.password.length > 5 ? '' : 'Passwored must be 6 char long'
            if (!this.passwordError) {
                console.log('Email', this.email)
                console.log('Password', this.password)
                console.log('Skills', this.Skills)
                console.log('Role', this.role)
                console.log('Term & Condition', this.term)


            }
        }
    },
};
</script>

<style>
    form {
    max-width: 420px;
    margin: 30px auto; 
    background: white; 
    text-align: left; 
    padding: 40px; 
    border-radius: 10px;
    }
label {
    color: #aaa; 
    display: inline-block; 
    margin: 25px 0 15px; 
    font-size: 0.6em; 
    text-transform: uppercase; 
    letter-spacing: 1px; 
    font-weight: bold;
}
input, select {
    display: block; 
    padding: 10px 6px; 
    width: 100%; 
    box-sizing: border-box; 
    border: none; 
    border-bottom: 1px solid #555; 
    color:#201e02;
}
input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}
.pills{
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}
button{
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
}
.submit{
    text-align:center;
}
.error{
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.8 rem;
    font-weight: bold;
}
</style>