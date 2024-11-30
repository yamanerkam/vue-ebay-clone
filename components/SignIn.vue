<template>
    <div class="sign-in-container">
      <h1>Sign in to your account</h1>
      <p class="new-user">
        New to eBay? <a href="#" class="create-link">Create account</a>
      </p>
  
      <form @submit.prevent="handleSubmit">
        <div class="input-wrapper">
          <input 
            type="text" 
            v-model="emailOrUsername" 
            placeholder="Email or username"
            required
          >
        </div>
  
        <button type="submit" class="continue-btn">Continue</button>
  
        <div class="divider">
          <span>or</span>
        </div>
  
        <div class="social-buttons">
          <button type="button" class="social-btn google">
            <img 
              src="https://ir.ebaystatic.com/rs/c/sgninui-src-static-images-google-logo-icon-PNG-Transparent-Background-Z_TFsqo3.png" 
              alt="Google"
              class="social-icon google-icon"
            />
            Continue with Google
          </button>
          <button type="button" class="social-btn facebook">
            <svg class="social-icon facebook-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
              <path fill="#1877F2" d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/>
            </svg>
            Continue with Facebook
          </button>
          <button type="button" class="social-btn apple">
            <svg class="social-icon apple-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512">
              <path d="M318.7 268.7c-.2-36.7 16.4-64.4 50-84.8-18.8-26.9-47.2-41.7-84.7-44.6-35.5-2.8-74.3 20.7-88.5 20.7-15 0-49.4-19.7-76.4-19.7C63.3 141.2 4 184.8 4 273.5q0 39.3 14.4 81.2c12.8 36.7 59 126.7 107.2 125.2 25.2-.6 43-17.9 75.8-17.9 31.8 0 48.3 17.9 76.4 17.9 48.6-.7 90.4-82.5 102.6-119.3-65.2-30.7-61.7-90-61.7-91.9zm-56.6-164.2c27.3-32.4 24.8-61.9 24-72.5-24.1 1.4-52 16.4-67.9 34.9-17.5 19.8-27.8 44.3-25.6 71.9 26.1 2 49.9-11.4 69.5-34.3z"/>
            </svg>
            Continue with Apple
          </button>
        </div>
  
        <div class="stay-signed">
          <label>
            <input type="checkbox" v-model="staySignedIn">
            Stay signed in
          </label>
          <button type="button" class="info-icon" @click="showInfo">ⓘ</button>
        </div>
      </form>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const emailOrUsername = ref('')
  const staySignedIn = ref(false)
  
  const handleSubmit = () => {
    console.log('Form submitted:', {
      emailOrUsername: emailOrUsername.value,
      staySignedIn: staySignedIn.value
    })
  }
  
  const showInfo = () => {
    alert('Stay signed in for faster purchasing next time')
  }
  </script>
  
  <style scoped>
  .sign-in-container {
    max-width: 300px;
    margin: 0 auto;
    padding: 20px;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  }
  
  h1 {
    font-size: 24px;
    text-align: center;
    margin-bottom: 8px;
    color: #111111;
  }
  
  .new-user {
    text-align: center;
    margin-bottom: 24px;
    color: #111111;
  }
  
  .create-link {
    color: inherit;
    text-decoration: none;
    font-weight: 500;
  }
  
  .create-link:hover {
    text-decoration: underline;
  }
  
  .input-wrapper input {
    width: 88%;
    padding: 12px 16px;
    border: 1px solid #ccc;
    border-radius: 8px;
    font-size: 16px;
    margin-bottom: 16px;
  }
  
  .input-wrapper input:focus {
    outline: none;
    border-color: #3665f3;
  }
  
  .continue-btn {
    width: 100%;
    padding: 12px;
    background-color: #3665f3;
    color: white;
    border: none;
    border-radius: 24px;
    font-size: 16px;
    cursor: pointer;
    margin-bottom: 16px;
  }
  
  .continue-btn:hover {
    background-color: #2b4fb4;
  }
  
  .divider {
    text-align: center;
    position: relative;
    margin: 20px 0;
  }
  
  .divider::before,
  .divider::after {
    content: '';
    position: absolute;
    top: 50%;
    width: 45%;
    height: 1px;
    background-color: #ccc;
  }
  
  .divider::before {
    left: 0;
  }
  
  .divider::after {
    right: 0;
  }
  
  .divider span {
    background-color: white;
    padding: 0 10px;
    color: #666;
    font-size: 14px;
  }
  
  .social-buttons {
    display: flex;
    flex-direction: column;
    gap: 8px;
    margin-bottom: 16px;
  }
  
  .social-btn {
    width: 100%;
    padding: 12px;
    border: 1px solid #333333;
    border-radius: 24px;
    background-color: white;
    font-size: 16px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
  }
  
  .social-btn:hover {
    background-color: #f5f5f5;
  }
  
  .social-icon {
    width: 18px;
    height: 18px;
    object-fit: contain;
  }
  
  .facebook-icon {
    width: 24px;
    height: 24px;
  }
  
  .apple-icon {
    width: 18px;
    height: 18px;
    fill: #000;
  }
  
  .stay-signed {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    font-size: 14px;
    margin-top: 16px;
  }
  
  .stay-signed input[type="checkbox"] {
    margin-right: 8px;
  }
  
  .info-icon {
    background: none;
    border: none;
    color: #666;
    cursor: pointer;
    padding: 0;
    font-size: 16px;
  }
  
  .info-icon:hover {
    color: #111;
  }
  </style>