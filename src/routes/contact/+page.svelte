<script>
    let name = "";
    let email = "";
    let subject = "";
    let content = "";

    const presetEmail = "rst4035@rit.edu";

    function sendEmail() {
        let body = "";
        if (name) body += `Name: ${name}\n`;
        if (email) body += `Email: ${email}\n`;
        body += `\n${content}`;

        const mailtoLink = `mailto:${presetEmail}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
        window.location.href = mailtoLink;
    }
</script>

<svelte:head>
    <title>Contact Us</title>
    <meta name="description" content="Contact Information for the Chinese Conversation Table" />
</svelte:head>

<div class="container">
    <div class="text-column">
        <h1>Contact Us</h1>

        <div class="contact-info">
            <p>Email Address: {presetEmail}</p>
            <p>Instagram: someInstagramName</p>
            <p>Campus Groups: ourCampusGroupLink</p>
        </div>

        <h2>Send us a message</h2>
        <form on:submit|preventDefault={sendEmail} class="contact-form">
            <label>
                Name (optional):
                <input type="text" bind:value={name}>
            </label>

            <label>
                Email (optional):
                <input type="email" bind:value={email}>
            </label>

            <label>
                Subject (optional):
                <input type="text" bind:value={subject}>
            </label>

            <label>
                Message:
                <textarea bind:value={content} required></textarea>
            </label>

            <button type="submit">Send Email</button>
        </form>
    </div>
</div>

<style>
    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        background: linear-gradient(to bottom right, #f0f4f8, #d9e2ec);
        font-family: Arial, sans-serif;
    }

    .text-column {
        background: white;
        padding: 2rem;
        border-radius: 12px;
        box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
        text-align: center;
        max-width: 400px;
        width: 100%;
    }

    .contact-info p {
        margin: 0.3rem 0;
        font-size: 0.95rem;
        color: #333;
    }

    .contact-form {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        margin-top: 1rem;
    }

    label {
        display: flex;
        flex-direction: column;
        font-size: 0.9rem;
        color: #555;
        text-align: left;
    }

    input, textarea {
        padding: 0.5rem;
        font-size: 1rem;
        border: 1px solid #ccc;
        border-radius: 6px;
        margin-top: 0.3rem;
        transition: border 0.2s;
    }

    input:focus, textarea:focus {
        border-color: #4a90e2;
        outline: none;
    }

    textarea {
        min-height: 100px;
        resize: vertical;
    }

    button {
        padding: 0.7rem;
        font-size: 1rem;
        color: white;
        background-color: #4a90e2;
        border: none;
        border-radius: 6px;
        cursor: pointer;
        transition: background 0.2s;
    }

    button:hover {
        background-color: #357ABD;
    }
</style>
