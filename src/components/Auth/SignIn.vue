<template>
    <div class="container">
        <div class="pixata-heading">Pixata</div>
        <form class="form-container" @submit.prevent="signIn()">
            <div class="quarter-circle"></div>
            <div class="heading">
                <div class="heading-signUp">Sign In</div>
            </div>
            <div>
                <div class="form-group">
                    <label for="username">Username</label>
                    <input
                        id="username"
                        type="text"
                        v-model="userName"
                        placeholder="johndoe7"
                    />
                </div>
                <div class="form-group">
                    <label for="password">Password</label>
                    <input
                        id="password"
                        type="password"
                        v-model="password"
                        placeholder="********"
                    />
                </div>
            </div>
            <div class="flex-col-center">
                <button
                    class="btn-submit"
                    type="submit"
                    :disabled="loading === true"
                >
                    <div v-if="!loading">
                        Sign In
                    </div>
                    <div v-else>
                        <Loader />
                    </div>
                </button>
                <p class="text-center">
                    New to Pixata?
                    <router-link to="/">SIGN UP</router-link>
                </p>
            </div>
            <div class="flower-circle"></div>
            <div class="leaf-one"></div>
            <div class="leaf-two"></div>
        </form>
    </div>
</template>
<script lang="ts">
/* eslint-disable */
import { defineComponent } from 'vue';
import axios from 'axios';

import Constant from '../../constant/Constant';
import Loader from '@/components/Loader/Loader.vue';

export default defineComponent({
    name: 'SignUp',
    components: {
        Loader,
    },
    data() {
        return {
            userName: '',
            password: '',
            loading: false,
            token: '',
            errMsg: '',
        };
    },
    methods: {
        async signIn() {
            this.loading = true;
            try {
                const res = await axios.post(`${Constant.baseUrl}user/signIn`, {
                    username: this.userName,
                    password: this.password,
                });
                this.loading = false;
                console.log(res);
            } catch (error) {
                this.loading = false;
                if (
                    error.message.includes('401') ||
                    error.message.includes('400')
                )
                    this.errMsg = 'Please check your username or password!';
                else this.errMsg = 'Something went wrong!';
            }
        },
    },
});
</script>

<style lang="scss">
.text-center {
    text-align: center;
}

.flex-center {
    display: flex;
    align-items: center;
    justify-content: center;
}

.flex-col-center {
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;
    margin: 1rem 0;
}

.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background: linear-gradient(45deg, #ffffff, #c1dedc);
}

.pixata-heading {
    text-align: center;
    margin: 1rem;
    font-size: 4rem;
    font-family: 'Dancing Script', cursive;
}

.quarter-circle {
    background: #268c83;
    width: 14%;
    border-radius: 25%;
    height: 12%;
    position: absolute;
    top: 0px;
    left: 0px;
    clip-path: circle(78.2% at 0 0);
}

.flower-circle {
    background: #268c8370;
    height: 40vh;
    width: 23vw;
    border-radius: 50% 0 5% 50%;
    position: absolute;
    right: 0px;
    clip-path: circle(50.6% at 99% 99%);
    bottom: 0px;
}

.leaf-one {
    background: #268c83;
    width: 75%;
    border-radius: 60%;
    height: 25%;
    position: absolute;
    bottom: 0px;
    -webkit-clip-path: circle(40% at 50% 100%);
    clip-path: circle(63% at 10% 177%);
}

.leaf-two {
    background: #268c83;
    width: 75%;
    border-radius: 60%;
    height: 25%;
    position: absolute;
    bottom: 0px;
    right: -35px;
    -webkit-clip-path: circle(40% at 50% 100%);
    clip-path: circle(61% at 10% 177%);
}

.heading {
    margin: 0.8rem 0;
    text-align: center;

    &-signUp {
        font-family: 'Dancing Script', cursive;
        text-align: center;
        color: #268c83;
        padding: 0px;
        font-weight: 800;
        font-size: 2.5rem;
    }
}

.form-container {
    width: 30%;
    padding: 2rem;
    position: relative;
    background-size: cover;
    background-position: center;
    height: 30rem;
    background: white;
    border-radius: 15px;
    box-shadow: 3px 3px 12px 2px #5a5858;

    label {
        width: 7rem;
        font-size: 0.9rem;
    }

    input[type='text'] {
        border: 1px solid #66bfb7;
        outline: none;
        padding: 8px;
        border-radius: 15px;
    }

    input[type='email'] {
        border: 1px solid #66bfb7;
        outline: none;
        padding: 8px;
        border-radius: 15px;
    }

    input[type='password'] {
        border: 1px solid #66bfb7;
        outline: none;
        padding: 8px;
        border-radius: 15px;
    }
}

.form-group {
    margin: 8px 0;
    display: flex;
    align-items: center;
    justify-content: center;
}

.btn-submit {
    padding: 10px;
    font-size: 1rem;
    margin: 12px;
    border: none;
    background: #268c83;
    color: white;
    border-radius: 15px;
    cursor: pointer;
    outline: none;

    &:disabled {
        background: gray;
        cursor: not-allowed;
    }

    // &:hover {
    //     background: white;
    //     color: #268c83;
    //     border: 1px solid #268c83;
    // }
}
</style>
