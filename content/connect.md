---js
const eleventyNavigation = {
  key: "Connect",
  order: 6
};
---

# Connect With Us

Whether you're beginning to sense there's a deeper mountain ahead, or you're ready to take the first step on your transformational journey, we'd love to hear from you.

## Start a Conversation

Reach out to explore how Mount Purpose can support your journey:

**Email:** [connect@mountpurpose.com](mailto:connect@mountpurpose.com)

---

## Join Our Community

Stay connected between gatherings, get early access to events, and join conversations with fellow travelers on the two-mountain journey.

**[Join Mount Purpose Community on Fabric →](https://mountpurpose.fabricapp.co)**

Fabric blends text messaging with event updates and community chat—making it easy to stay in the loop without another app to download.

---

## Subscribe to Purpose Matters

Receive insights, reflections, and guidance for navigating your two-mountain journey.

<div class="message-box" style="margin: 2em 0;">
  <h3 style="margin-top: 0;">Purpose Matters Newsletter</h3>
  <p>Wisdom for leaders navigating the transition from success to significance.</p>
  
  <form class="klaviyo-form" id="newsletter-form" style="display: flex; flex-direction: column; gap: 1.25em; max-width: 500px; margin-top: 1.5em;">
    <input type="text" name="first_name" placeholder="First Name" required style="padding: 1em; border: 2px solid var(--color-border); border-radius: 4px; font-family: var(--font-family); font-size: 1rem; background-color: rgba(255,255,255,0.9); width: 100%;">
    
    <input type="email" name="email" placeholder="Your best email address" required style="padding: 1em; border: 2px solid var(--color-border); border-radius: 4px; font-family: var(--font-family); font-size: 1rem; background-color: rgba(255,255,255,0.9); width: 100%;">
    
    <button type="submit" style="padding: 1em 2em; background-color: var(--color-monarch-gold); color: var(--color-forest-floor); border: none; border-radius: 4px; font-family: var(--font-family-display); font-size: 1.125rem; font-weight: 600; cursor: pointer; transition: background-color 0.2s; width: 100%;">Subscribe</button>
    
    <p id="form-message" style="margin: 0; font-size: 0.95rem; display: none;"></p>
  </form>
</div>

<script>
document.getElementById('newsletter-form').addEventListener('submit', async function(e) {
  e.preventDefault();
  
  const form = e.target;
  const button = form.querySelector('button');
  const message = document.getElementById('form-message');
  const firstName = form.querySelector('[name="first_name"]').value;
  const email = form.querySelector('[name="email"]').value;
  
  // Disable button and show loading state
  button.disabled = true;
  button.textContent = 'Subscribing...';
  message.style.display = 'none';
  
  try {
    const response = await fetch('https://a.klaviyo.com/client/subscriptions/?company_id=U5CBFS', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'revision': '2024-07-15'
      },
      body: JSON.stringify({
        data: {
          type: 'subscription',
          attributes: {
            profile: {
              data: {
                type: 'profile',
                attributes: {
                  email: email,
                  first_name: firstName
                }
              }
            },
            custom_source: 'Mount Purpose Website'
          },
          relationships: {
            list: {
              data: {
                type: 'list',
                id: 'TJh6ev'
              }
            }
          }
        }
      })
    });
    
    if (response.ok || response.status === 202) {
      message.textContent = '🎉 Welcome! Check your email to confirm your subscription.';
      message.style.color = 'var(--text-color)';
      message.style.display = 'block';
      form.reset();
    } else {
      const errorData = await response.json();
      console.error('Klaviyo error:', errorData);
      throw new Error('Subscription failed');
    }
  } catch (error) {
    console.error('Form error:', error);
    message.textContent = 'Something went wrong. Please try again or email us directly.';
    message.style.color = '#c5534f';
    message.style.display = 'block';
  } finally {
    button.disabled = false;
    button.textContent = 'Subscribe';
  }
});
</script>

---

*Every journey begins with connection. We're honored you're considering us as guides for yours.*