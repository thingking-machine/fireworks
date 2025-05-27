---
layout: home
title: Thingking Machine
---
# Thingking Machine

<pre>
  A machine is a <b>thing</b>. Things can not <b>think</b>. ...but some of them can <b>thingk</b>!
</pre>

<style>
  .llm-param-form {
    margin-top: 20px;
    padding: 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
  }
  /* Removed .llm-param-form h2 styling as the h2 is removed */

  .llm-param-form .form-row { /* New class for each label-input pair row */
    display: flex;
    align-items: center; /* Vertically align items in the middle */
    margin-bottom: 10px; /* Space between rows */
  }

  .llm-param-form label {
    /* display: block; */ /* No longer needed */
    /* margin-top: 10px; */ /* No longer needed */
    font-weight: bold;
    margin-right: 10px; /* Space between label and input */
    min-width: 150px; /* Adjust as needed for your longest label */
    text-align: right; /* Optional: align label text to the right */
  }

  .llm-param-form input[type="text"],
  .llm-param-form input[type="number"],
  .llm-param-form select {
    width: 100%; /* Input will take remaining space within its flex container */
    max-width: 300px;
    padding: 8px;
    /* margin-top: 5px; */ /* No longer needed as alignment is handled by flex */
    border: 1px solid #ddd;
    border-radius: 4px;
    box-sizing: border-box;
  }

  .styled-link-button {
    display: inline-block;
    padding: 10px 18px;
    margin-top: 20px; /* This can be adjusted or moved to a wrapper div if needed */
    background-color: #007bff;
    color: white !important; /* Important to override default link styles */
    text-decoration: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1em;
    text-align: center;
    border: none;
  }
  .styled-link-button:hover {
    background-color: #0056b3;
    text-decoration: none;
  }
</style>

<div class="llm-param-form">
  <!-- Removed <h2>Set LLM Parameters</h2> -->
  <form id="llmParamsForm">
    <div class="form-row"> <!-- Added form-row class -->
      <label for="model">Model:</label>
      <input type="text" id="model" name="model" value="gpt-4-turbo">
    </div>
    <div class="form-row"> <!-- Added form-row class -->
      <label for="temperature">Temperature:</label>
      <input type="number" id="temperature" name="temperature" value="0.7" step="0.1" min="0" max="2">
    </div>
    <div class="form-row"> <!-- Added form-row class -->
      <label for="max_tokens">Max Tokens:</label>
      <input type="number" id="max_tokens" name="max_tokens" value="2000" step="100">
    </div>
    <div class="form-row"> <!-- Added form-row class -->
      <label for="system_prompt">System Prompt (optional):</label>
      <input type="text" id="system_prompt" name="system_prompt" value="You are a helpful assistant.">
    </div>
    <div> <!-- This div can remain as is for the button, or you can add form-row and adjust alignment if needed -->
      <a href="#" id="navigateToMachineLink" class="styled-link-button">Thingk with these settings!</a>
    </div>
  </form>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const navigateLink = document.getElementById('navigateToMachineLink');
  if (navigateLink) {
    navigateLink.addEventListener('click', function(event) {
        event.preventDefault();
        const form = document.getElementById('llmParamsForm');
        const params = {};
        new FormData(form).forEach((value, key) => {
        if (value) {
            params[key] = value;
        }
      });

      const queryParams = new URLSearchParams(params);

      // Construct the target URL using Jekyll's relative_url filter for robustness
      const targetBaseUrl = "{{ '/pages/machine' | relative_url }}";
      const targetUrl = targetBaseUrl + '?' + queryParams.toString();
      
      window.location.href = targetUrl;
    });
  }
});
</script>
