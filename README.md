<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Doctor Barista - Coffee Shop</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        /* Global Styles */
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background: #f4f4f9;
            color: #333;
            overflow-x: hidden;
        }

        /* Interactive Background */
        .hero-section {
            background: linear-gradient(135deg, rgba(169, 111, 52, 0.8), rgba(211, 168, 85, 0.8)), url('https://via.placeholder.com/1920x1080/7a4b2f/ffffff?text=Coffee+Shop+Background');
            background-size: cover;
            background-position: center;
            padding: 120px 0;
            text-align: center;
            color: white;
            position: relative;
            z-index: 1;
        }

        .hero-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.3);
            z-index: -1;
        }

        h1, h2 {
            color: white;
        }

        #menu .card {
            border: none;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }

        #menu .card:hover {
            transform: translateY(-10px);
        }

        #menu .card-img-top {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 20px;
        }

        button {
            margin-top: 10px;
        }

        /* Form Styles */
        #contact-form input, #contact-form textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
        }

        /* Price and Order Styles */
        .order-summary {
            margin-top: 20px;
            font-size: 1.2em;
        }

        .order-summary p {
            margin: 5px 0;
        }

        /* Animation Styles */
        .fade-in {
            animation: fadeIn 0.5s ease-out;
        }

        .scale-up {
            animation: scaleUp 0.3s ease-out;
        }

        @keyframes fadeIn {
            0% {
                opacity: 0;
            }
            100% {
                opacity: 1;
            }
        }

        @keyframes scaleUp {
            0% {
                transform: scale(0.9);
            }
            100% {
                transform: scale(1);
            }
        }

        .list-group-item {
            transition: transform 0.3s ease, background-color 0.3s ease;
        }

        .list-group-item:hover {
            transform: scale(1.05);
            background-color: #f8f9fa;
        }

        /* Scrolling Animations */
        @keyframes parallax {
            0% {
                background-position: 0% 0%;
            }
            100% {
                background-position: 100% 100%;
            }
        }

        .parallax {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('https://via.placeholder.com/1920x1080/7a4b2f/ffffff?text=Coffee+Shop+Background') no-repeat center center fixed;
            background-size: cover;
            animation: parallax 10s infinite linear;
            z-index: -2;
        }
    </style>
</head>
<body>
    <!-- Parallax Background -->
    <div class="parallax"></div>

    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark sticky-top">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Doctor Barista</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item"><a class="nav-link" href="#menu">Menu</a></li>
                    <li class="nav-item"><a class="nav-link" href="#order">Order Now</a></li>
                    <li class="nav-item"><a class="nav-link" href="#contact">Contact</a></li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <header class="hero-section">
        <h1>Welcome to Doctor Barista</h1>
        <p>Your Favorite Coffee, Delivered Fast</p>
        <a href="#menu" class="btn btn-primary">Explore Menu</a>
    </header>

    <!-- Menu Section -->
    <section id="menu" class="container my-5">
        <h2 class="text-center">Our Menu</h2>
        <div class="row g-4">
            <div class="col-md-4">
                <div class="card">
                    <img src="https://via.placeholder.com/300" class="card-img-top" alt="Espresso">
                    <div class="card-body text-center">
                        <h5 class="card-title">Espresso</h5>
                        <p class="card-text">$2.00</p>
                        <button class="btn btn-primary" onclick="addToOrder('Espresso', 2.00)">Add to Order</button>
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="card">
                    <img src="https://via.placeholder.com/300" class="card-img-top" alt="Cappuccino">
                    <div class="card-body text-center">
                        <h5 class="card-title">Cappuccino</h5>
                        <p class="card-text">$3.00</p>
                        <button class="btn btn-primary" onclick="addToOrder('Cappuccino', 3.00)">Add to Order</button>
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="card">
                    <img src="https://via.placeholder.com/300" class="card-img-top" alt="Latte">
                    <div class="card-body text-center">
                        <h5 class="card-title">Latte</h5>
                        <p class="card-text">$3.50</p>
                        <button class="btn btn-primary" onclick="addToOrder('Latte', 3.50)">Add to Order</button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Order Section -->
    <section id="order" class="container my-5">
        <h2>Your Order</h2>
        <ul id="order-list" class="list-group"></ul>
        <div class="order-summary">
            <p><strong>Total: $<span id="total-price">0.00</span></strong></p>
        </div>
        <button class="btn btn-success" onclick="placeOrder()">Place Order</button>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="container my-5">
        <h2>Contact Us</h2>
        <form id="contact-form">
            <input type="text" id="name" placeholder="Your Name" required><br>
            <input type="email" id="email" placeholder="Your Email" required><br>
            <textarea id="message" placeholder="Your Message" required></textarea><br>
            <button type="submit" class="btn btn-primary">Send</button>
        </form>
    </section>

    <!-- Footer -->
    <footer>
        <p>&copy; 2024 Doctor Barista. All rights reserved.</p>
    </footer>

    <script>
        // Handle Orders
        const orderList = document.getElementById('order-list');
        const totalPriceElement = document.getElementById('total-price');
        let totalPrice = 0;

        function addToOrder(item, price) {
            const listItem = document.createElement('li');
            listItem.className = 'list-group-item d-flex justify-content-between align-items-center fade-in scale-up';
            listItem.textContent = item + " - $" + price.toFixed(2);

            const removeButton = document.createElement('button');
            removeButton.className = 'btn btn-danger btn-sm';
            removeButton.textContent = 'Remove';
            removeButton.onclick = () => {
                totalPrice -= price;
                totalPriceElement.textContent = totalPrice.toFixed(2);
                listItem.remove();
            };

            listItem.appendChild(removeButton);
            orderList.appendChild(listItem);

            totalPrice += price;
            totalPriceElement.textContent = totalPrice.toFixed(2);
        }

        function placeOrder() {
            alert('Your order has been placed!');
            orderList.innerHTML = '';
            totalPrice = 0;
            totalPriceElement.textContent = '0.00';
        }
    </script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
