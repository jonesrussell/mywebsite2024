<script>
  let email = '';
  let name = '';
  let comments = '';

  function handleSubmit() {
    // Handle form submission logic here
    console.log('Email:', email);
    console.log('Name:', name);
    console.log('Comments:', comments);
  }
</script>

<section>
  <h2>Newsletter Signup</h2>
  <form on:submit|preventDefault={handleSubmit}>
    <label>
      Email:
      <input bind:value={email} type="email" required />
    </label>
    <label>
      Name:
      <input bind:value={name} type="text" required />
    </label>
    <label>
      Comments:
      <textarea bind:value={comments}></textarea>
    </label>
    <button type="submit">Sign Up</button>
  </form>
</section>