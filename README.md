<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Art Showroom</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Quicksand:wght@400;600&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Quicksand', sans-serif; margin: 0; padding: 0; background: linear-gradient(#fce4ec, #e1bee7); color: #4a4a4a; }
        header { background: #ffb3ba; color: #fff; padding: 1rem; text-align: center; border-radius: 0 0 20px 20px; }
        .header-content { display: flex; justify-content: space-between; align-items: center; }
        .header-left h1 { margin: 0; font-family: 'Dancing Script', cursive; font-size: 2rem; }
        .header-right { font-size: 1.2rem; font-weight: bold; font-family: 'Dancing Script', cursive; }
        nav { margin-top: 1rem; display: flex; justify-content: center; }
        nav a { color: #fff; margin: 0 1rem; text-decoration: none; padding: 0.5rem; border-radius: 20px; background: rgba(255,255,255,0.2); }
        .gallery { display: flex; flex-wrap: wrap; justify-content: center; padding: 2rem; }
        .art-piece { margin: 1rem; text-align: center; width: 300px; background: rgba(255,255,255,0.8); padding: 1rem; border-radius: 15px; }
        .art-piece img { width: 100%; height: 200px; object-fit: cover; border: 2px solid #ffb3ba; border-radius: 10px; }
        .art-piece button { margin-top: 0.5rem; padding: 0.5rem; background: #ff9a9e; color: white; border: none; cursor: pointer; border-radius: 20px; }
        .about, .contact { padding: 2rem; max-width: 800px; margin: auto; background: rgba(255,255,255,0.9); border-radius: 20px; margin-bottom: 2rem; }
        .about h2, .contact h2 { font-family: 'Dancing Script', cursive; color: #e91e63; }
        form { display: flex; flex-direction: column; }
        input, textarea { margin-bottom: 1rem; padding: 0.5rem; border: 1px solid #ffb3ba; border-radius: 10px; }
        button { padding: 0.5rem; background: #ff9a9e; color: white; border: none; cursor: pointer; border-radius: 20px; }
        .cart { padding: 2rem; background: rgba(255,255,255,0.9); margin: 2rem auto; max-width: 800px; border-radius: 20px; }
        .cart h2 { font-family: 'Dancing Script', cursive; color: #e91e63; }
        .cart-item { display: flex; justify-content: space-between; margin-bottom: 0.5rem; padding: 0.5rem; background: #fce4ec; border-radius: 10px; }
        footer { text-align: center; padding: 1rem; background: #ffb3ba; color: #fff; font-family: 'Dancing Script', cursive; border-radius: 20px 20px 0 0; }
        @media (max-width: 768px) { nav { flex-direction: column; } .gallery { padding: 1rem; } .art-piece { width: 100%; max-width: 300px; } .header-content { flex-direction: column; } }
    </style>
</head>
<body>
    <header>
        <div class="header-content">
            <div class="header-left">
                <h1>Welcome to Our Art Showroom 💖</h1>
            </div>
            <div class="header-right">
                Javeria Artology Store 🌸
            </div>
        </div>
        <nav>
            <a href="#gallery">Gallery</a>
            <a href="#about">About</a>
            <a href="#contact">Contact</a>
            <a href="#cart">Cart</a>
        </nav>
    </header>

    <section id="gallery" class="gallery">
        <div class="art-piece">
            <img src="https://raw.githubusercontent.com/javeriamedical-cloud/artshowroom/main/WhatsApp%20Image%202026-02-09%20at%204.55.05%20PM.jpeg" alt="Artwork 1" width="285" height="190" />
            <p>Acrylic sunset Painting - RS. 1000</p>
            <button onclick="addToCart('Acrylic sunset Painting', 1000)">Add to Cart</button>
        </div>
        <div class="art-piece">
            <img src="https://raw.githubusercontent.com/javeriamedical-cloud/artshowroom/main/bubble.jpeg" alt="Artwork 2" width="300" height="200" />
            <p>Acrylic bubble painting - RS. 1000</p>
            <button onclick="addToCart('Acrylic bubble painting', 1000)">Add to Cart</button>
        </div>
        <div class="art-piece">
            <img src="https://raw.githubusercontent.com/javeriamedical-cloud/artshowroom/main/candle.jpeg" alt="Artwork 3" width="281" height="187" />
            <p>Acrylic realistic rain painting - RS. 1000</p>
            <button onclick="addToCart('Acrylic realistic rain painting', 1000)">Add to Cart</button>
        </div>
    </section>

    <section id="about" class="about">
        <h2>About Us</h2>
        <p>We showcase contemporary art from emerging and established artists. Our showroom features paintings, sculptures, and digital works. Visit us to discover your next favorite piece! ✨</p>
    </section>

    <section id="contact" class="contact">
        <h2>Contact Us</h2>
        <form id="contactForm">
            <input type="text" placeholder="Your Name" required>
            <input type="email" placeholder="Your Email" required>
            <textarea placeholder="Your Message" required></textarea>
            <button type="submit">Send</button>
        </form>
    </section>

    <section id="cart" class="cart">
        <h2>Your Shopping Cart</h2>
        <div id="cartItems"></div>
        <p>Total: RS.<span id="cartTotal">0</span></p>
        <button onclick="checkout()">Checkout</button>
    </section>

    <footer>
        Dream big, create bigger! 💕 Javeria Artology Store
    </footer>

    <script>
        let cart = JSON.parse(localStorage.getItem('cart')) || [];
        updateCartDisplay();

        function addToCart(name, price) {
            cart.push({ name, price });
            localStorage.setItem('cart', JSON.stringify(cart));
            updateCartDisplay();
            alert(name + ' added to cart! 💖');
        }

        function updateCartDisplay() {
            const cartItems = document.getElementById('cartItems');
            const cartTotal = document.getElementById('cartTotal');
            cartItems.innerHTML = '';
            let total = 0;
            cart.forEach(item => {
                const div = document.createElement('div');
                div.className = 'cart-item';
                div.innerHTML = `<span>${item.name}</span><span>RS.${item.price}</span>`;
                cartItems.appendChild(div);
                total += item.price;
            });
            cartTotal.textContent = total;
        }

        function checkout() {
            if (cart.length === 0) {
                alert('Your cart is empty! 😊');
            } else {
                alert('Checkout successful! Total: RS.' + document.getElementById('cartTotal').textContent + ' 🌸');
                cart = [];
                localStorage.setItem('cart', JSON.stringify(cart));
                updateCartDisplay();
            }
        }

        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Thank you for your message! We will get back to you soon. 💕');
        });
    </script>
</body>
</html>

