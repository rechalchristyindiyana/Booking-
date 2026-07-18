```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome to Sea Zoe Beach Homes</title>
    <style>
        :root {
            --primary: #2b7a78;
            --secondary: #3aafa9;
            --background: #feffff;
            --text: #17252a;
            --light-bg: #f3f9f9;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--light-bg);
            color: var(--text);
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .card {
            background: var(--background);
            padding: 30px;
            border-radius: 16px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
            max-width: 450px;
            width: 100%;
            box-sizing: border-box;
        }

        .header {
            text-align: center;
            margin-bottom: 25px;
        }

        .header h1 {
            font-size: 24px;
            margin: 10px 0 5px 0;
            color: var(--primary);
        }

        .header p {
            font-size: 14px;
            color: #666;
            margin: 0;
        }

        .welcome-text {
            font-size: 15px;
            line-height: 1.5;
            color: #444;
            margin-bottom: 25px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            font-size: 14px;
            font-weight: 600;
            margin-bottom: 8px;
            color: var(--text);
        }

        input[type="date"], select {
            width: 100%;
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 8px;
            font-size: 16px;
            box-sizing: border-box;
            background-color: #fff;
            color: var(--text);
        }

        input[type="date"]:focus, select:focus {
            outline: none;
            border-color: var(--secondary);
            box-shadow: 0 0 0 3px rgba(58, 175, 169, 0.2);
        }

        .btn-submit {
            width: 100%;
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 14px;
            font-size: 16px;
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            transition: background 0.2s;
            margin-top: 10px;
        }

        .btn-submit:hover {
            background-color: #1f5e5c;
        }

        .quick-links {
            margin-top: 25px;
            padding-top: 20px;
            border-top: 1px solid #eee;
        }

        .quick-links h3 {
            font-size: 14px;
            margin: 0 0 12px 0;
            color: #777;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .link-item {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
            text-decoration: none;
            color: var(--primary);
            font-weight: 500;
            font-size: 15px;
        }

        .link-item span {
            margin-right: 10px;
        }

        .link-item:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>

<div class="card">
    <div class="header">
        <span style="font-size: 40px;">🌊🏡</span>
        <h1>Sea Zoe Beach Homes</h1>
        <p>Staycation Escape</p>
    </div>

    <p class="welcome-text">
        Thank you for reaching out! We would love to host your next staycation. Please select your preferred dates and guest count below to check availability.
    </p>

    <form id="bookingForm">
        <div class="form-group">
            <label for="checkin">📅 Check-in Date</label>
            <input type="date" id="checkin" required>
        </div>

        <div class="form-group">
            <label for="checkout">📅 Check-out Date</label>
            <input type="date" id="checkout" required>
        </div>

        <div class="form-group">
            <label for="guests">👥 Number of Guests</label>
            <select id="guests" required>
                <option value="1">1 Guest</option>
                <option value="2">2 Guests</option>
                <option value="3">3 Guests</option>
                <option value="4">4 Guests</option>
                <option value="5">5 Guests</option>
                <option value="6+">6+ Guests</option>
            </select>
        </div>

        <button type="submit" class="btn-submit">Check Availability</button>
    </form>

    <div class="quick-links">
        <h3>📍 Quick Links & Info</h3>
        <!-- REPLACE THE '#' LINKS BELOW WITH YOUR ACTUAL LINKS -->
        <a href="https://www.instagram.com/seazoebeachhomes" target="_blank" class="link-item">
            <span>📋</span> View Our Rates & Amenities
        </a>
        <a href="https://maps.app.goo.gl/ApqjgyVZi6NJgEkq9" target="_blank" class="link-item">
            <span>📍</span> Location & Directions
        </a>
    </div>
</div>

<script>
    // Set minimum date to today so guests can't pick past dates
    const today = new Date().toISOString().split('T')[0];
    document.getElementById('checkin').min = today;
    document.getElementById('checkout').min = today;

    // Dynamically adjust checkout minimum date based on checkin choice
    document.getElementById('checkin').addEventListener('change', function() {
        document.getElementById('checkout').min = this.value;
    });

    // Handle form submission and format a WhatsApp response
    document.getElementById('bookingForm').addEventListener('submit', function(e) {
        e.preventDefault();
        
        const checkin = document.getElementById('checkin').value;
        const checkout = document.getElementById('checkout').value;
        const guests = document.getElementById('guests').value;

        // Custom message format that will be sent back to you
        const message = `Hii, Sea Zoe Beach Homes Staycation! I'd like to check availability for a staycation:\n\n📅 Check-in: ${checkin}\n📅 Check-out: ${checkout}\n👥 Guests: ${guests}`;
        
        // Encode message for URL use
        const encodedMessage = encodeURIComponent(message);
        
        // Replace with your actual WhatsApp Business number (include country code, no + or spaces)
        const whatsappNumber ="919490675816"; 
        
        // Redirect back to WhatsApp with filled info
        window.location.href = `https://wa.me/${whatsappNumber}?text=${encodedMessage}`;
    });
</script>

</body>
</html>

```
