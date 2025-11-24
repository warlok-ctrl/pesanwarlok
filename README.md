<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Menu Makanan - Pesan Sekarang</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #ffffff;
            min-height: 100vh;
            padding: 20px;
            position: relative;
        }

        body::before {
            content: '👑';
            position: fixed;
            top: 20px;
            left: 20px;
            font-size: 3em;
            opacity: 0.3;
            z-index: 0;
        }

        body::after {
            content: '👑';
            position: fixed;
            top: 20px;
            right: 20px;
            font-size: 3em;
            opacity: 0.3;
            z-index: 0;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        header {
            text-align: center;
            color: #333;
            margin-bottom: 40px;
            padding: 30px;
            background: linear-gradient(135deg, #FFF8DC 0%, #FAEBD7 100%);
            border-radius: 20px;
            box-shadow: 0 5px 20px rgba(139, 69, 19, 0.1);
            border: 3px solid #D2691E;
            position: relative;
        }

        header::before {
            content: '⚜️';
            position: absolute;
            top: 10px;
            left: 30px;
            font-size: 2em;
            opacity: 0.4;
        }

        header::after {
            content: '⚜️';
            position: absolute;
            top: 10px;
            right: 30px;
            font-size: 2em;
            opacity: 0.4;
        }

None

        header p {
            font-size: 1.2em;
            opacity: 0.9;
        }

        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        .menu-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(139, 69, 19, 0.15);
            transition: transform 0.3s ease;
            border: 2px solid #D2691E;
            position: relative;
        }

        .menu-card::before {
            content: '✨';
            position: absolute;
            top: 10px;
            right: 10px;
            font-size: 1.5em;
            z-index: 1;
            opacity: 0.6;
        }

        .menu-card:hover {
            transform: translateY(-5px);
        }

        .menu-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, #8B4513 0%, #D2691E 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4em;
        }

        .menu-content {
            padding: 20px;
        }

        .menu-content h3 {
            color: #333;
            margin-bottom: 10px;
            font-size: 1.5em;
        }

        .menu-content p {
            color: #666;
            margin-bottom: 15px;
            line-height: 1.6;
        }

        .price {
            color: #8B4513;
            font-size: 1.5em;
            font-weight: bold;
            margin-bottom: 15px;
        }

        .quantity-control {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 15px;
        }

        .quantity-control button {
            width: 35px;
            height: 35px;
            border: none;
            background: #8B4513;
            color: white;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.2em;
            transition: background 0.3s;
        }

        .quantity-control button:hover {
            background: #D2691E;
        }

        .quantity-control span {
            min-width: 30px;
            text-align: center;
            font-weight: bold;
            font-size: 1.2em;
        }

        .order-btn {
            width: 100%;
            padding: 12px;
            background: linear-gradient(135deg, #8B4513 0%, #D2691E 100%);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1em;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .order-btn:hover {
            transform: scale(1.05);
        }

        .cart {
            background: linear-gradient(135deg, #FFF8DC 0%, #FAEBD7 100%);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(139, 69, 19, 0.15);
            position: sticky;
            top: 20px;
            border: 3px solid #D2691E;
        }

        .cart h2 {
            color: #333;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #8B4513;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px solid #eee;
        }

        .cart-item:last-child {
            border-bottom: none;
        }

        .cart-item-name {
            font-weight: 500;
        }

        .cart-item-qty {
            color: #666;
            font-size: 0.9em;
        }

        .cart-item-price {
            color: #8B4513;
            font-weight: bold;
        }

        .cart-total {
            margin-top: 20px;
            padding-top: 20px;
            border-top: 2px solid #8B4513;
            display: flex;
            justify-content: space-between;
            font-size: 1.3em;
            font-weight: bold;
            color: #333;
        }

        .checkout-btn {
            width: 100%;
            padding: 15px;
            margin-top: 20px;
            background: linear-gradient(135deg, #8B4513 0%, #D2691E 100%);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1.1em;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .checkout-btn:hover {
            transform: scale(1.05);
        }

        .checkout-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .empty-cart {
            text-align: center;
            color: #999;
            padding: 20px;
        }

        @media (max-width: 768px) {
            header h1 {
                font-size: 2em;
            }
            
            .menu-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>👑 WARLOK 👑</h1>
            <p>⚜️ WARUNG LOKAL ⚜️</p>
        </header>

        <div class="menu-grid">
            <div class="menu-card">
                <div class="menu-image">🍛</div>
                <div class="menu-content">
                    <h3>Rendang Sultan</h3>
                    <p>Rendang daging sapi empuk dengan bumbu rempah istimewa ala sultan</p>
                    <div class="price">Rp 20.000</div>
                    <div class="quantity-control">
                        <button onclick="decreaseQty(0)">-</button>
                        <span id="qty-0">0</span>
                        <button onclick="increaseQty(0)">+</button>
                    </div>
                    <button class="order-btn" onclick="addToCart(0)">Tambah ke Keranjang</button>
                </div>
            </div>

            <div class="menu-card">
                <div class="menu-image">🍢</div>
                <div class="menu-content">
                    <h3>Sate Orang Kaya</h3>
                    <p>Sate ayam/kambing premium dengan bumbu kacang khas yang lezat</p>
                    <div class="price">Rp 15.000</div>
                    <div class="quantity-control">
                        <button onclick="decreaseQty(1)">-</button>
                        <span id="qty-1">0</span>
                        <button onclick="increaseQty(1)">+</button>
                    </div>
                    <button class="order-btn" onclick="addToCart(1)">Tambah ke Keranjang</button>
                </div>
            </div>

            <div class="menu-card">
                <div class="menu-image">🍳</div>
                <div class="menu-content">
                    <h3>Nasi Goreng Spesial</h3>
                    <p>Nasi goreng dengan telur, ayam, dan bumbu rahasia yang menggugah selera</p>
                    <div class="price">Rp 15.000</div>
                    <div class="quantity-control">
                        <button onclick="decreaseQty(2)">-</button>
                        <span id="qty-2">0</span>
                        <button onclick="increaseQty(2)">+</button>
                    </div>
                    <button class="order-btn" onclick="addToCart(2)">Tambah ke Keranjang</button>
                </div>
            </div>

            <div class="menu-card">
                <div class="menu-image">🥗</div>
                <div class="menu-content">
                    <h3>Gado² Orang Jogja</h3>
                    <p>Sayuran segar dengan bumbu kacang kental khas Yogyakarta yang autentik</p>
                    <div class="price">Rp 12.000</div>
                    <div class="quantity-control">
                        <button onclick="decreaseQty(3)">-</button>
                        <span id="qty-3">0</span>
                        <button onclick="increaseQty(3)">+</button>
                    </div>
                    <button class="order-btn" onclick="addToCart(3)">Tambah ke Keranjang</button>
                </div>
            </div>

            <div class="menu-card">
                <div class="menu-image">🍤</div>
                <div class="menu-content">
                    <h3>Pempek Palembang</h3>
                    <p>Pempek ikan asli Palembang dengan cuko yang pedas manis menyegarkan</p>
                    <div class="price">Rp 10.000</div>
                    <div class="quantity-control">
                        <button onclick="decreaseQty(4)">-</button>
                        <span id="qty-4">0</span>
                        <button onclick="increaseQty(4)">+</button>
                    </div>
                    <button class="order-btn" onclick="addToCart(4)">Tambah ke Keranjang</button>
                </div>
            </div>

            <div class="menu-card">
                <div class="menu-image">🍲</div>
                <div class="menu-content">
                    <h3>Gudeg Enak</h3>
                    <p>Gudeg manis dengan nangka muda, ayam, dan telur khas Jogja yang lezat</p>
                    <div class="price">Rp 12.000</div>
                    <div class="quantity-control">
                        <button onclick="decreaseQty(5)">-</button>
                        <span id="qty-5">0</span>
                        <button onclick="increaseQty(5)">+</button>
                    </div>
                    <button class="order-btn" onclick="addToCart(5)">Tambah ke Keranjang</button>
                </div>
            </div>

            <div class="menu-card">
                <div class="menu-image">🍜</div>
                <div class="menu-content">
                    <h3>Rawon Sapi</h3>
                    <p>Sup daging sapi hitam dengan kluwak khas Jawa Timur yang menggoda</p>
                    <div class="price">Rp 11.000</div>
                    <div class="quantity-control">
                        <button onclick="decreaseQty(6)">-</button>
                        <span id="qty-6">0</span>
                        <button onclick="increaseQty(6)">+</button>
                    </div>
                    <button class="order-btn" onclick="addToCart(6)">Tambah ke Keranjang</button>
                </div>
            </div>

            <div class="menu-card">
                <div class="menu-image">🥘</div>
                <div class="menu-content">
                    <h3>Soto Betawi</h3>
                    <p>Soto santan khas Jakarta dengan daging sapi dan jeroan yang gurih</p>
                    <div class="price">Rp 10.000</div>
                    <div class="quantity-control">
                        <button onclick="decreaseQty(7)">-</button>
                        <span id="qty-7">0</span>
                        <button onclick="increaseQty(7)">+</button>
                    </div>
                    <button class="order-btn" onclick="addToCart(7)">Tambah ke Keranjang</button>
                </div>
            </div>
        </div>

        <div class="cart">
            <h2>🛒 Keranjang Pesanan</h2>
            <div id="cart-items">
                <div class="empty-cart">Keranjang masih kosong</div>
            </div>
            <div id="cart-total" style="display: none;">
                <div class="cart-total">
                    <span>Total:</span>
                    <span id="total-price">Rp 0</span>
                </div>
                <button class="checkout-btn" onclick="checkout()">Pesan Sekarang</button>
            </div>
        </div>
    </div>

    <script>
        const menuItems = [
            { name: 'Rendang Sultan', price: 20000, emoji: '🍛' },
            { name: 'Sate Orang Kaya', price: 15000, emoji: '🍢' },
            { name: 'Nasi Goreng Spesial', price: 15000, emoji: '🍳' },
            { name: 'Gado-Gado Orang Jogja', price: 12000, emoji: '🥗' },
            { name: 'Pempek Palembang', price: 10000, emoji: '🍤' },
            { name: 'Gudeg Enak', price: 12000, emoji: '🍲' },
            { name: 'Rawon Sapi', price: 11000, emoji: '🍜' },
            { name: 'Soto Betawi', price: 10000, emoji: '🥘' }
        ];

        let quantities = [0, 0, 0, 0, 0, 0, 0, 0];
        let cart = [];

        function increaseQty(index) {
            quantities[index]++;
            document.getElementById(`qty-${index}`).textContent = quantities[index];
        }

        function decreaseQty(index) {
            if (quantities[index] > 0) {
                quantities[index]--;
                document.getElementById(`qty-${index}`).textContent = quantities[index];
            }
        }

        function addToCart(index) {
            if (quantities[index] > 0) {
                const existingItem = cart.find(item => item.index === index);
                if (existingItem) {
                    existingItem.quantity += quantities[index];
                } else {
                    cart.push({
                        index: index,
                        name: menuItems[index].name,
                        price: menuItems[index].price,
                        quantity: quantities[index],
                        emoji: menuItems[index].emoji
                    });
                }
                quantities[index] = 0;
                document.getElementById(`qty-${index}`).textContent = 0;
                updateCart();
            }
        }

        function updateCart() {
            const cartItemsDiv = document.getElementById('cart-items');
            const cartTotalDiv = document.getElementById('cart-total');

            if (cart.length === 0) {
                cartItemsDiv.innerHTML = '<div class="empty-cart">Keranjang masih kosong</div>';
                cartTotalDiv.style.display = 'none';
                return;
            }

            let html = '';
            let total = 0;

            cart.forEach((item, idx) => {
                const itemTotal = item.price * item.quantity;
                total += itemTotal;
                html += `
                    <div class="cart-item">
                        <div>
                            <div class="cart-item-name">${item.emoji} ${item.name}</div>
                            <div class="cart-item-qty">${item.quantity} x ${formatPrice(item.price)}</div>
                        </div>
                        <div class="cart-item-price">${formatPrice(itemTotal)}</div>
                    </div>
                `;
            });

            cartItemsDiv.innerHTML = html;
            document.getElementById('total-price').textContent = formatPrice(total);
            cartTotalDiv.style.display = 'block';
        }

        function formatPrice(price) {
            return 'Rp ' + price.toLocaleString('id-ID');
        }

        function checkout() {
            if (cart.length === 0) return;

            let message = 'Pesanan Anda:%0A%0A';
            let total = 0;

            cart.forEach(item => {
                const itemTotal = item.price * item.quantity;
                total += itemTotal;
                message += `${item.emoji} ${item.name}%0A`;
                message += `   ${item.quantity} x ${formatPrice(item.price)} = ${formatPrice(itemTotal)}%0A%0A`;
            });

            message += `Total: ${formatPrice(total)}%0A%0A`;
            message += 'Terima kasih telah memesan!';

            
            const phoneNumber = '6281211557540'; // Nomor WhatsApp Warlok
            window.open(`https://wa.me/${phoneNumber}?text=${message}`, '_blank');

            
            cart = [];
            quantities = [0, 0, 0, 0, 0, 0, 0, 0];
            updateCart();
        }
    </script>
</body>
</html>
