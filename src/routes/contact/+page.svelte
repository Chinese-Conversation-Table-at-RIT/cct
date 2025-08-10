<script>
  import emailjs from 'emailjs-com';

  let name = '';
  let email = '';
  let message = '';
  let status = '';

  const SERVICE_ID = 'service_jkq5b3u';
  const TEMPLATE_ID = 'template_pkf9tia';
  const PUBLIC_KEY = 'Rck1sjqBH0dNeF-aW';

  const sendEmail = async () => {
    if (!name || !email || !message) {
      status = "Please fill in all fields.";
      return;
    }

    try {
      await emailjs.send(
        SERVICE_ID,
        TEMPLATE_ID,
        { from_name: name, from_email: email, message },
        PUBLIC_KEY
      );
      status = "✅ Message sent successfully!";
      name = email = message = '';
    } catch (error) {
      console.error("Email send error:", error);
      status = "❌ Failed to send message. Try again.";
    }
  };
</script>

<div class="contact-container">
  <h2>📧 Send Me a Message</h2>
  <input type="text" placeholder="Your Gmail Name" bind:value={name} />
  <input type="email" placeholder="Your Gmail Address" bind:value={email} />
  <textarea placeholder="Your message..." bind:value={message}></textarea>
  <button on:click={sendEmail}>Send</button>
  {#if status}
    <p class="status">{status}</p>
  {/if}
</div>

<style>
  .contact-container {
    max-width: 400px;
    margin: auto;
    padding: 2rem;
    background: #fff;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    display: flex;
    flex-direction: column;
    gap: 1rem;
    font-family: system-ui, sans-serif;
  }
  h2 {
    text-align: center;
    margin-bottom: 1rem;
  }
  input, textarea {
    padding: 0.8rem;
    border-radius: 8px;
    border: 1px solid #ccc;
    font-size: 1rem;
    width: 100%;
  }
  textarea {
    resize: none;
    height: 100px;
  }
  button {
    background: #1a73e8;
    color: white;
    padding: 0.8rem;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1rem;
    transition: background 0.2s;
  }
  button:hover {
    background: #155ab6;
  }
  .status {
    text-align: center;
    font-weight: bold;
  }
</style>
