<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Art Showroom</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Quicksand:wght@400;600&display=swap" rel="stylesheet">
    <style>
        body { 
            font-family: 'Quicksand', sans-serif; 
            margin: 0; 
            padding: 0; 
            background: 
                radial-gradient(circle, rgba(139, 69, 19, 0.1) 1px, transparent 1px), /* Dark pink dots */
                linear-gradient(#fce4ec, #ffb3ba), /* Light pink gradient */
                url('https://images.unsplash.com/photo-1518709268805-4e9042af2176?w=1920'); /* Mini flower pattern */
            background-size: 20px 20px, cover, cover; 
            background-attachment: fixed; 
            color: #4a4a4a; 
        }
        header { background: rgba(255, 179, 186, 0.9); color: #fff; padding: 1rem; text-align: center; border-radius: 0 0 20px 20px; }
        .header-content { display: flex; justify-content: space-between; align-items: center; }
        .header-left h1 { margin: 0; font-family: 'Dancing Script', cursive; font-size: 2rem; }
        .header-right { font-size: 1.2rem; font-weight: bold; font-family: 'Dancing Script', cursive; }
        nav { margin-top: 1rem; display: flex; justify-content: center; }
        nav a { color: #fff; margin: 0 1rem; text-decoration: none; padding: 0.5rem; border-radius: 20px; background: rgba(255,255,255,0.2); }
        .top-controls { display: flex; justify-content: center; align-items: center; margin-top: 1rem; gap: 1rem; }
        .top-controls input { padding: 0.5rem; border: 1px solid #ffb3ba; border-radius: 20px; width: 200px; }
        .top-controls button { padding: 0.5rem 1rem; background: rgba(255,255,255,0.2); color: #fff; border: none; cursor: pointer; border-radius: 20px; font-weight: bold; }
        .gallery { display: flex; flex-wrap: wrap; justify-content: center; padding: 2rem; }
        .gallery.list-view .art-piece { width: 100%; max-width: none; display: flex; align-items: center; margin: 0.5rem 0; padding: 1rem; }
        .gallery.list-view .art-piece img { width: 100px; height: 100px; margin-right: 1rem; }
        .gallery.list-view .art-piece p { margin: 0; flex-grow: 1; }
        .gallery.list-view .quantity, .gallery.list-view .add-btn { margin-left: 1rem; }
        .art-piece { margin: 1rem; text-align: center; width: 300px; background: rgba(255,255,255,0.9); padding: 1rem; border-radius: 15px; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
        .art-piece img { width: 100%; height: 200px; object-fit: cover; border: 2px solid #ffb3ba; border-radius: 10px; }
        .quantity { display: flex; align-items: center; justify-content: center; margin: 0.5rem 0; }
        .quantity button { width: 30px; height: 30px; background: #ff9a9e; color: white; border: none; cursor: pointer; border-radius: 50%; font-size: 1.2rem; }
        .quantity span { margin: 0 1rem; font-weight: bold; }
        .art-piece .add-btn { margin-top: 0.5rem; padding: 0.5rem; background: #ff9a9e; color: white; border: none; cursor: pointer; border-radius: 20px; }
        .about, .contact { padding: 2rem; max-width: 800px; margin: auto; background: rgba(255,255,255,0.9); border-radius: 20px; margin-bottom: 2rem; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
        .about h2, .contact h2 { font-family: 'Dancing Script', cursive; color: #e91e63; }
        form { display: flex; flex-direction: column; }
        input, textarea { margin-bottom: 1rem; padding: 0.5rem; border: 1px solid #ffb3ba; border-radius: 10px; }
        button { padding: 0.5rem; background: #ff9a9e; color: white; border: none; cursor: pointer; border-radius: 20px; }
        .cart { padding: 2rem; background: rgba(255,255,255,0.9); margin: 2rem auto; max-width: 800px; border-radius: 20px; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
        .cart h2 { font-family: 'Dancing Script', cursive; color: #e91e63; }
        .cart-item { display: flex; justify-content: space-between; align-items: center; margin-bottom: 0.5rem; padding: 0.5rem; background: #fce4ec; border-radius: 10px; }
        .cart-item .quantity { margin: 0; }
        .showcase { padding: 2rem; text-align: center; background: rgba(255,255,255,0.9); margin: 2rem auto; max-width: 800px; border-radius: 20px; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
        .showcase h2 { font-family: 'Dancing Script', cursive; color: #e91e63; }
        .slideshow { position: relative; width: 100%; max-width: 500px; margin: auto; overflow: hidden; border-radius: 15px; }
        .slideshow img { width: 100%; height: 300px; object-fit: cover; display: none; }
        .slideshow img.active { display: block; }
        footer { text-align: center; padding: 1rem; background: rgba(255, 179, 186, 0.9); color: #fff; font-family: 'Dancing Script', cursive; border-radius: 20px 20px 0 0; }
        @media (max-width: 768px) { nav { flex-direction: column; } .gallery { padding: 1rem; } .art-piece { width: 100%; max-width: 300px; } .header-content { flex-direction: column; } .slideshow img { height: 200px; } .top-controls { flex-direction: column; gap: 0.5rem; } .top-controls input { width: 100%; } }
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
            <a href="#showcase">Showcase</a>
        </nav>
        <div class="top-controls">
            <input type="text" id="searchInput" placeholder="Search art...">
            <button id="listViewBtn">📋 List View</button>
            <button id="cartBtn">🛒 Cart (<span id="cartCount">0</span>)</button>
        </div>
    </header>

    <section id="gallery" class="gallery">
        <div class="art-piece">
            <img src="https://raw.githubusercontent.com/javeriamedical-cloud/artshowroom/main/WhatsApp%20Image%202026-02-09%20at%204.55.05%20PM.jpeg" alt="Artwork 1" width="285" height="190" />
            <p>Acrylic sunset Painting - RS. 1000</p>
            <div class="quantity">
                <button onclick="changeQuantity(this, -1)">-</button>
                <span>1</span>
                <button onclick="changeQuantity(this, 1)">+</button>
            </div>
            <button class="add-btn" onclick="addToCart('Acrylic sunset Painting', 1000, this.previousElementSibling.querySelector('span').textContent)">Add to Cart</button>
        </div>
        <div class="art-piece">
            <img src="https://raw.githubusercontent.com/javeriamedical-cloud/artshowroom/main/bubble.jpeg" alt="Artwork 2" width="300" height="200" />
            <p>Acrylic bubble painting - RS. 1000</p>
            <div class="quantity">
                <button onclick="changeQuantity(this, -1)">-</button>
                <span>1</span>
                <button onclick="changeQuantity(this, 1)">+</button>
            </div>
            <button class="add-btn" onclick="addToCart('Acrylic bubble painting', 1000, this.previousElementSibling.querySelector('span').textContent)">Add to Cart</button>
        </div>
        <div class="art-piece">
            <img src="https://raw.githubusercontent.com/javeriamedical-cloud/artshowroom/main/candle.jpeg" alt="Artwork 3" width="281" height="187" />
            <p>Acrylic realistic rain painting - RS. 1000</p>
            <div class="quantity">
                <button onclick="changeQuantity(this, -1)">-</button>
                <span>1</span>
                <button onclick="changeQuantity(this, 1)">+</button>
            </div>
            <button class="add-btn" onclick="addToCart('Acrylic realistic rain painting', 1000, this.previousElementSibling.querySelector('span').textContent)">Add to Cart</button>
        </div>
    </section>

    <section id="about" class="about">
        <h2>About Us</h2>
        <p>We showcase contemporary art from emerging and established artists. Our showroom features paintings, sculptures, and digital works. Visit us to discover your next favorite piece! ✨</p>
        <p><strong>Delivery time: 5 to 7 days. Buy above RS. 2000 and get free delivery.</strong></p>
        <p><strong>Business Hours: 10am - 6pm Monday to Sunday</strong></p>
    </section>

    <section id="contact" class="contact">
        <h2>Contact Us</h2>
        <p>Phone: 0318-1133708</p>
        <p><a href="https://wa.me/923181133708" target="_blank" style="color: #25d366; text-decoration: none; font-weight: bold;">📱 Message or Call on WhatsApp</a></p>
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
        <!-- ✅ ADDED MESSAGE (ONLY ADDITION) -->
        <p style="text-align:center; margin-top:1rem; font-weight:bold; color:#e91e63;">
            Thank you for shopping, visit again 💖
        </p>
    </section>

    <section id="showcase" class="showcase">
        <h2>Art Showcase 🎨</h2>
        <p>Enjoy a slideshow of our beautiful art pieces!</p>
        <div class="slideshow">
            <img src="https://raw.githubusercontent.com/javeriamedical-cloud/artshowroom/main/WhatsApp%20Image%202026-02-09%20at%204.55.05%20PM.jpeg" alt="Artwork 1" class="active">
            <img src="https://raw.githubusercontent.com/javeriamedical-cloud/artshowroom/main/bubble.jpeg" alt="Artwork 2">
            <img src="https://raw.githubusercontent.com/javeriamedical-cloud/artshowroom/main/candle.jpeg" alt="Artwork 3">
        </div>
    </section>

    <footer>
        Dream big, create bigger! 💕 Javeria Artology Store<br>
        Email: javeriamedical@gmail.com
    </footer>

    <script>
        let cart = JSON.parse(localStorage.getItem('cart')) || [];
        updateCartDisplay();

        function changeQuantity(button, delta) {
            const span = button.parentElement.querySelector('span');
            let qty = parseInt(span.textContent);
            qty = Math.max(1, qty + delta);
            span.textContent = qty;
        }

        function addToCart(name, price, qty) {
            qty = parseInt(qty);
            const existing = cart.find(item => item.name === name);
            if (existing) {
                existing.qty += qty;
            } else {
                cart.push({ name, price, qty });
            }
            localStorage.setItem('cart', JSON.stringify(cart));
            updateCartDisplay();
            alert(`${qty} x ${name} added to cart! 💖`);
        }

        function updateCartDisplay() {
            const cartItems = document.getElementById('cartItems');
            const cartTotal = document.getElementById('cartTotal');
            const cartCount = document.getElementById('cartCount');
            cartItems.innerHTML = '';
            let total = 0;
            let count = 0;
            cart.forEach((item, index) => {
                const div = document.createElement('div');
                div.className = 'cart-item';
                div.innerHTML = `
                    <span>${item.name} (Qty: ${item.qty})</span>
                    <div class="quantity">
                        <button onclick="changeCartQuantity(${index}, -1)">-</button>
                        <span>${item.qty}</span>
                        <button onclick="changeCartQuantity(${index}, 1)">+</button>
                    </div>
                    <span>RS.${item.price * item.qty}</span>
                    <button onclick="removeFromCart(${index})">Remove</button>
                `;
                cartItems.appendChild(div);
                total += item.price * item.qty;
                count += item.qty;
            });
            cartTotal.textContent = total;
            cartCount.textContent = count;
        }

        function changeCartQuantity(index, delta) {
            cart[index].qty = Math.max(1, cart[index].qty + delta);
            localStorage.setItem('cart', JSON.stringify(cart));
            updateCartDisplay();
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            localStorage.setItem('cart', JSON.stringify(cart));
            updateCartDisplay();
        }

        function checkout() {
            if (cart.length === 0) {
                alert('Your cart is empty! 😊');
                return;
            }
            let message = 'Hi, I want to order:\n';
            cart.forEach(item => {
                message += `- ${item.name} (Qty: ${item.qty}) - RS.${item.price * item.qty}\n`;
            });
            message += `Total: RS.${document.getElementById('cartTotal').textContent}\nPlease confirm delivery details.`;
            const whatsappUrl = `https://wa.me/923181133708?text=${encodeURIComponent(message)}`;
            window.open(whatsappUrl, '_blank');
            cart = [];
            localStorage.setItem('cart', JSON.stringify(cart));
            updateCartDisplay();
            alert('Order sent to WhatsApp! 💖');
        }

        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Thank you for your message! We will get back to you soon. 💕');
        });

        // Slideshow for showcase
        let slideIndex = 0;
        const slides = document.querySelectorAll('.slideshow img');
        function showSlides() {
            slides.forEach(slide => slide.classList.remove('active'));
            slideIndex = (slideIndex + 1) % slides.length;
            slides[slideIndex].classList.add('active');
        }
        setInterval(showSlides, 3000); // Change image every 3 seconds

        // Search functionality
        document.getElementById('searchInput').addEventListener('input', function() {
            const query = this.value.toLowerCase();
            const artPieces = document.querySelectorAll('.art-piece');
            artPieces.forEach(piece => {
                const text = piece.querySelector('p').textContent.toLowerCase();
                if (text.includes(query)) {
                    piece.style.display = 'block';
                } else {
                    piece.style.display = 'none';
                }
            });
        });

        // List view toggle
        document.getElementById('listViewBtn').addEventListener('click', function() {
            const gallery = document.querySelector('.gallery');
            gallery.classList.toggle('list-view');
            this.textContent = gallery.classList.contains('list-view') ? '🔲 Grid View' : '📋 List View';
        });

        // Cart button click to scroll to cart
        document.getElementById('cartBtn').addEventListener('click', function() {
            document.getElementById('cart').scrollIntoView({ behavior: 'smooth' });
        });
    </script>
</body>
</html>
