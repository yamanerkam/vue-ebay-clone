<template>
    <nav class="nav-bar">
      <div class="nav-left">
        <span>Hi! <a href="#">Sign in</a> or <a href="#">register</a></span>
        <a href="#">Daily Deals</a>
        <a href="#">Help & Contact</a>
      </div>
      <div class="nav-right">
        <span>Ship to</span>
        <a href="#">Sell</a>
        <div class="dropdown">
          <button>Watchlist <span>▼</span></button>
        </div>
        <div class="dropdown">
          <button>My eBay <span>▼</span></button>
        </div>
        <button>🔔</button>
        <button>🛒</button>
      </div>
    </nav>
  </template>
  
  <script setup>
  // No script needed for this static version
  </script>
  
  <style scoped>
  .nav-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 8px 16px;
    font-family: Arial, sans-serif;
    font-size: 12px;
    border-bottom: 1px solid #e5e5e5;
  }
  
  .nav-left, .nav-right {
    display: flex;
    align-items: center;
    gap: 16px;
  }
  
  a {
    color: #0053a0;
    text-decoration: none;
  }
  
  button {
    background: none;
    border: none;
    cursor: pointer;
    font-size: 12px;
    padding: 0;
  }
  
  .dropdown button {
    display: flex;
    align-items: center;
  }
  
  .dropdown span {
    font-size: 8px;
    margin-left: 4px;
  }
  </style>