<template>
    <section class="login-form">
        <div class="login-form-title">
            <h2>Login Form</h2>
        </div>

        <vee-form id="login-form-details" :validation-schema="loginSchema">
            <label for="email">Email:</label>
            <vee-field type="email" id="email" name="email" placeholder="Enter your mail id" />
            <ErrorMessage class="error-text" name="email" />

            <label for="password">Password:</label>
            <vee-field type="password" id="password" name="password" placeholder="Enter your password" />
            <ErrorMessage class="error-text" name="password" />

            <div class="buttons">
                <button type="reset" class="cancel-btn" @click="onCancel">Cancel</button>
                <button type="submit" class="login-btn" @login="login">Login</button>
            </div>
        </vee-form>
    </section>
</template>


<script>
import { ErrorMessage } from "vee-validate";

export default {
    name: "LoginForm",

    data() {
        return {
            loginSchema: {
                email: "required|email",
                password: "required|min:8|max:12|regex:^(?=.*\\d)(?=.*[^\\w\\d\\s]).+$",
            },
        };
    },
}
</script>

<style scoped>
.login-form {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    margin-top: 15%;
    border-radius: 20px;
}

h2 {
    text-align: center;
    color: white;
}

label {
    display: block;
    margin-bottom: 10px;
}

input[type="email"],
input[type="password"] {
    width: 100%;
    padding: 8px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

input[type="radio"] {
    margin-right: 5px;
}

.login-btn {
    border: none;
    background-color: #4caf50;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    float: right;
}

.cancel-btn {
    border: none;
    background-color: red;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    float: left;
}

.buttons {
    display: flex;
    justify-content: space-between;
}

#login-form-details {
    color: white;
}


.error-text {
    color: rgb(219, 81, 81);
}

/* Responsive Styles */
@media (max-width: 500px) {
    .container {
        max-width: 100%;
    }
}
</style>
