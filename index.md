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
  .llm-param-form h2 {
    margin-top: 0;
  }
  .llm-param-form label {
    display: block;
    margin-top: 10px;
    font-weight: bold;
  }
  .llm-param-form input[type="text"],
  .llm-param-form input[type="number"],
  .llm-param-form select {
    width: 100%;
    max-width: 300px;
    padding: 8px;
    margin-top: 5px;
    border: 1px solid #ddd;
    border-radius: 4px;
    box-sizing: border-box;
  }
  .styled-link-button {
    display: inline-block;
    padding: 10px 18px;
    margin-top: 20px;
    background-color: #007bff;
    color: white !important; /* Important to override default link styles */
    text-decoration: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1em;
    text-align: center;
    border: none; /* If it were an input type=submit */
  }
  .styled-link-button:hover {
    background-color: #0056b3;
    text-decoration: none;
  }
</style>

<div class="llm-param-form">
  <h2>Set LLM Parameters</h2>
  <form id="llmParamsForm">
    <div>
      <label for="model">Model:</label>
      <input type="text" id="model" name="model" value="gpt-4-turbo">
    </div>
    <div>
      <label for="temperature">Temperature:</label>
      <input type="number" id="temperature" name="temperature" value="0.7" step="0.1" min="0" max="2">
    </div>
    <div>
      <label for="max_tokens">Max Tokens:</label>
      <input type="number" id="max_tokens" name="max_tokens" value="2000" step="100">
    </div>
    <div>
      <label for="system_prompt">System Prompt (optional):</label>
      <input type="text" id="system_prompt" name="system_prompt" value="You are a helpful assistant.">
    </div>
    <div>
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
