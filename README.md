<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NURA FASHION - TOKO FASHION NURUL</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        header {
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            margin-bottom: 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }

        .logo {
            font-size: 28px;
            font-weight: bold;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .cart-btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
            transition: transform 0.3s;
            position: relative;
        }

        .cart-btn:hover {
            transform: translateY(-2px);
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background: #ff4757;
            color: white;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 12px;
            font-weight: bold;
        }

        .search-bar {
            width: 100%;
            margin-top: 15px;
        }

        .search-bar input {
            width: 100%;
            padding: 12px 20px;
            border: 2px solid #e0e0e0;
            border-radius: 25px;
            font-size: 14px;
            outline: none;
        }

        .filters {
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            margin-bottom: 30px;
        }

        .filter-buttons {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .filter-btn {
            padding: 10px 20px;
            border: 2px solid #667eea;
            background: white;
            color: #667eea;
            border-radius: 20px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 600;
            transition: all 0.3s;
        }

        .filter-btn.active {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        .product-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            transition: transform 0.3s;
        }

        .product-card:hover {
            transform: translateY(-10px);
        }

        .product-image {
            width: 100%;
            height: 300px;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 80px;
        }

        .product-info {
            padding: 20px;
        }

        .product-category {
            color: #667eea;
            font-size: 12px;
            font-weight: 600;
            text-transform: uppercase;
            margin-bottom: 8px;
        }

        .product-name {
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 10px;
        }

        .product-price {
            font-size: 24px;
            font-weight: bold;
            color: #764ba2;
            margin-bottom: 15px;
        }

        .add-to-cart {
            width: 100%;
            padding: 12px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 14px;
            font-weight: bold;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.7);
            z-index: 1000;
            align-items: center;
            justify-content: center;
            padding: 20px;
            overflow-y: auto;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            border-radius: 20px;
            padding: 30px;
            max-width: 600px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid #e0e0e0;
        }

        .modal-title {
            font-size: 24px;
            font-weight: bold;
            color: #333;
        }

        .close-btn {
            background: none;
            border: none;
            font-size: 30px;
            cursor: pointer;
            color: #999;
        }

        .cart-item {
            display: flex;
            gap: 15px;
            padding: 15px;
            border-bottom: 1px solid #e0e0e0;
            align-items: center;
        }

        .cart-item-icon {
            font-size: 40px;
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .cart-item-info {
            flex: 1;
        }

        .cart-item-name {
            font-weight: bold;
            margin-bottom: 5px;
        }

        .cart-item-price {
            color: #764ba2;
            font-weight: bold;
        }

        .cart-item-remove {
            background: #ff4757;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 12px;
        }

        .cart-total {
            margin-top: 20px;
            padding-top: 20px;
            border-top: 2px solid #e0e0e0;
        }

        .total-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
            font-size: 16px;
        }

        .total-row.grand-total {
            font-size: 20px;
            font-weight: bold;
            color: #764ba2;
            margin-top: 10px;
            padding-top: 10px;
            border-top: 2px solid #e0e0e0;
        }

        .checkout-btn, .continue-btn {
            width: 100%;
            margin-top: 20px;
            padding: 15px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
        }

        .form-section {
            margin-bottom: 25px;
        }

        .form-title {
            font-size: 18px;
            font-weight: bold;
            color: #764ba2;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #333;
        }

        .form-group input,
        .form-group textarea,
        .form-group select {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 14px;
            outline: none;
            transition: border 0.3s;
        }

        .form-group input:focus,
        .form-group textarea:focus,
        .form-group select:focus {
            border-color: #667eea;
        }

        .form-group textarea {
            resize: vertical;
            min-height: 80px;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        .payment-methods {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }

        .payment-method {
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            padding: 15px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
        }

        .payment-method:hover {
            border-color: #667eea;
            background: #f8f9ff;
        }

        .payment-method.active {
            border-color: #667eea;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .payment-method-icon {
            font-size: 32px;
            margin-bottom: 8px;
        }

        .payment-method-name {
            font-size: 13px;
            font-weight: 600;
        }

        .order-summary {
            background: #f8f9ff;
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
        }

        .order-summary-title {
            font-size: 16px;
            font-weight: bold;
            color: #764ba2;
            margin-bottom: 15px;
        }

        .summary-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 14px;
        }

        .back-btn {
            width: 100%;
            margin-top: 10px;
            padding: 12px;
            background: #e0e0e0;
            color: #333;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 14px;
            font-weight: bold;
        }

        .empty-cart {
            text-align: center;
            padding: 40px 20px;
            color: #999;
        }

        .empty-cart-icon {
            font-size: 60px;
            margin-bottom: 15px;
        }

        .success-icon {
            font-size: 80px;
            text-align: center;
            margin-bottom: 20px;
        }

        .success-message {
            text-align: center;
            margin-bottom: 20px;
        }

        .success-message h2 {
            color: #00C851;
            margin-bottom: 10px;
        }

        .order-details {
            background: #f8f9ff;
            padding: 20px;
            border-radius: 15px;
            margin: 20px 0;
        }

        .order-detail-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
            padding-bottom: 10px;
            border-bottom: 1px solid #e0e0e0;
        }

        .order-detail-row:last-child {
            border-bottom: none;
        }

        @media (max-width: 768px) {
            .products-grid {
                grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            }

            .product-image {
                height: 200px;
                font-size: 50px;
            }

            .form-row {
                grid-template-columns: 1fr;
            }

            .payment-methods {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">🛍️ Fashion Nurul</div>
            <button class="cart-btn" onclick="toggleCart()">
                🛒 Keranjang
                <span class="cart-count" id="cartCount">0</span>
            </button>
            <div class="search-bar">
                <input type="text" id="searchInput" placeholder="Cari produk fashion..." onkeyup="searchProducts()">
            </div>
        </header>

        <div class="filters">
            <div class="filter-buttons">
                <button class="filter-btn active" onclick="filterProducts('all')">Semua</button>
                <button class="filter-btn" onclick="filterProducts('pakaian')">Pakaian</button>
                <button class="filter-btn" onclick="filterProducts('sepatu')">Sepatu</button>
                <button class="filter-btn" onclick="filterProducts('aksesoris')">Aksesoris</button>
                <button class="filter-btn" onclick="filterProducts('tas')">Tas</button>
            </div>
        </div>

        <div class="products-grid" id="productsGrid"></div>
    </div>

    <div class="modal" id="cartModal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">🛒 Keranjang Belanja</div>
                <button class="close-btn" onclick="toggleCart()">&times;</button>
            </div>
            <div id="cartItems"></div>
            <div class="cart-total">
                <div class="total-row">
                    <span>Subtotal:</span>
                    <span id="subtotalAmount">Rp 0</span>
                </div>
                <div class="total-row">
                    <span>Ongkir:</span>
                    <span id="shippingAmount">Rp 0</span>
                </div>
                <div class="total-row grand-total">
                    <span>Total:</span>
                    <span id="totalAmount">Rp 0</span>
                </div>
            </div>
            <button class="checkout-btn" onclick="proceedToCheckout()">Lanjut ke Pembayaran</button>
        </div>
    </div>

    <div class="modal" id="checkoutModal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">📦 Checkout</div>
                <button class="close-btn" onclick="closeCheckout()">&times;</button>
            </div>

            <div class="form-section">
                <div class="form-title">📍 Alamat Pengiriman</div>
                <div class="form-group">
                    <label>Nama Lengkap *</label>
                    <input type="text" id="fullName" placeholder="Masukkan nama lengkap" required>
                </div>
                <div class="form-group">
                    <label>Nomor Telepon *</label>
                    <input type="tel" id="phone" placeholder="08xxxxxxxxxx" required>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>Provinsi *</label>
                        <select id="province" onchange="updateShipping()">
                            <option value="">Pilih Provinsi</option>
                            <option value="jawa-barat">Jawa Barat</option>
                            <option value="jawa-tengah">Jawa Tengah</option>
                            <option value="jawa-timur">Jawa Timur</option>
                            <option value="dki-jakarta">DKI Jakarta</option>
                            <option value="banten">Banten</option>
                            <option value="luar-jawa">Luar Jawa</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>Kota/Kabupaten *</label>
                        <input type="text" id="city" placeholder="Kota/Kabupaten" required>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>Kecamatan</label>
                        <input type="text" id="district" placeholder="Kecamatan">
                    </div>
                    <div class="form-group">
                        <label>Kode Pos</label>
                        <input type="text" id="postalCode" placeholder="Kode Pos">
                    </div>
                </div>
                <div class="form-group">
                    <label>Alamat Lengkap *</label>
                    <textarea id="address" placeholder="Jalan, RT/RW, No. Rumah, Patokan" required></textarea>
                </div>
            </div>

            <div class="form-section">
                <div class="form-title">💳 Metode Pembayaran</div>
                <div class="payment-methods">
                    <div class="payment-method" onclick="selectPayment('cod')">
                        <div class="payment-method-icon">💵</div>
                        <div class="payment-method-name">COD</div>
                    </div>
                    <div class="payment-method" onclick="selectPayment('transfer')">
                        <div class="payment-method-icon">🏦</div>
                        <div class="payment-method-name">Transfer Bank</div>
                    </div>
                    <div class="payment-method" onclick="selectPayment('ewallet')">
                        <div class="payment-method-icon">📱</div>
                        <div class="payment-method-name">E-Wallet</div>
                    </div>
                    <div class="payment-method" onclick="selectPayment('credit')">
                        <div class="payment-method-icon">💳</div>
                        <div class="payment-method-name">Kartu Kredit</div>
                    </div>
                </div>
            </div>

            <div class="order-summary">
                <div class="order-summary-title">📋 Ringkasan Pesanan</div>
                <div id="checkoutSummary"></div>
                <div class="summary-item" style="margin-top: 15px; padding-top: 15px; border-top: 2px solid #ddd;">
                    <strong>Total Pembayaran:</strong>
                    <strong id="checkoutTotal" style="color: #764ba2;">Rp 0</strong>
                </div>
            </div>

            <button class="continue-btn" onclick="completeOrder()">Bayar Sekarang</button>
            <button class="back-btn" onclick="backToCart()">Kembali ke Keranjang</button>
        </div>
    </div>

    <div class="modal" id="successModal">
        <div class="modal-content">
            <div class="success-icon">✅</div>
            <div class="success-message">
                <h2>Pesanan Berhasil!</h2>
                <p>Terima kasih telah berbelanja di Fashion Nurul</p>
            </div>
            <div class="order-details" id="orderDetails"></div>
            <button class="continue-btn" onclick="closeSuccess()">Kembali Belanja</button>
        </div>
    </div>

    <script>
        const products = [
            { id: 1, name: 'Dress Elegan', category: 'pakaian', price: 350000, icon: '👗' },
            { id: 2, name: 'Kemeja Formal', category: 'pakaian', price: 275000, icon: '👔' },
            { id: 3, name: 'Celana Jeans', category: 'pakaian', price: 299000, icon: '👖' },
            { id: 4, name: 'Jaket Denim', category: 'pakaian', price: 425000, icon: '🧥' },
            { id: 5, name: 'Kaos Casual', category: 'pakaian', price: 150000, icon: '👕' },
            { id: 6, name: 'Sneakers Sport', category: 'sepatu', price: 550000, icon: '👟' },
            { id: 7, name: 'High Heels', category: 'sepatu', price: 475000, icon: '👠' },
            { id: 8, name: 'Sepatu Boots', category: 'sepatu', price: 625000, icon: '👢' },
            { id: 9, name: 'Tas Ransel', category: 'tas', price: 399000, icon: '🎒' },
            { id: 10, name: 'Tas Tangan', category: 'tas', price: 450000, icon: '👜' },
            { id: 11, name: 'Kacamata Hitam', category: 'aksesoris', price: 225000, icon: '🕶️' },
            { id: 12, name: 'Topi Baseball', category: 'aksesoris', price: 125000, icon: '🧢' }
        ];

        let cart = [];
        let currentFilter = 'all';
        let currentSearch = '';
        let selectedPayment = '';
        let shippingCost = 0;

        function renderProducts() {
            const grid = document.getElementById('productsGrid');
            let filteredProducts = products;

            if (currentFilter !== 'all') {
                filteredProducts = filteredProducts.filter(p => p.category === currentFilter);
            }

            if (currentSearch) {
                filteredProducts = filteredProducts.filter(p => 
                    p.name.toLowerCase().includes(currentSearch.toLowerCase())
                );
            }

            grid.innerHTML = filteredProducts.map(product => `
                <div class="product-card">
                    <div class="product-image">${product.icon}</div>
                    <div class="product-info">
                        <div class="product-category">${product.category}</div>
                        <div class="product-name">${product.name}</div>
                        <div class="product-price">Rp ${product.price.toLocaleString('id-ID')}</div>
                        <button class="add-to-cart" onclick="addToCart(${product.id})">Tambah ke Keranjang</button>
                    </div>
                </div>
            `).join('');
        }

        function filterProducts(category) {
            currentFilter = category;
            document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');
            renderProducts();
        }

        function searchProducts() {
            currentSearch = document.getElementById('searchInput').value;
            renderProducts();
        }

        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const existingItem = cart.find(item => item.id === productId);

            if (existingItem) {
                existingItem.quantity++;
            } else {
                cart.push({ ...product, quantity: 1 });
            }

            updateCart();
            event.target.textContent = '✓ Ditambahkan!';
            setTimeout(() => event.target.textContent = 'Tambah ke Keranjang', 1000);
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCart();
        }

        function updateCart() {
            const cartCount = document.getElementById('cartCount');
            const cartItems = document.getElementById('cartItems');

            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            cartCount.textContent = totalItems;

            if (cart.length === 0) {
                cartItems.innerHTML = '<div class="empty-cart"><div class="empty-cart-icon">🛒</div><div>Keranjang kosong</div></div>';
                document.getElementById('subtotalAmount').textContent = 'Rp 0';
                document.getElementById('shippingAmount').textContent = 'Rp 0';
                document.getElementById('totalAmount').textContent = 'Rp 0';
                return;
            }

            cartItems.innerHTML = cart.map(item => `
                <div class="cart-item">
                    <div class="cart-item-icon">${item.icon}</div>
                    <div class="cart-item-info">
                        <div class="cart-item-name">${item.name}</div>
                        <div class="cart-item-price">Rp ${item.price.toLocaleString('id-ID')} x ${item.quantity}</div>
                    </div>
                    <button class="cart-item-remove" onclick="removeFromCart(${item.id})">Hapus</button>
                </div>
            `).join('');

            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const shipping = 15000;
            const total = subtotal + shipping;

            document.getElementById('subtotalAmount').textContent = `Rp ${subtotal.toLocaleString('id-ID')}`;
            document.getElementById('shippingAmount').textContent = `Rp ${shipping.toLocaleString('id-ID')}`;
            document.getElementById('totalAmount').textContent = `Rp ${total.toLocaleString('id-ID')}`;
        }

        function toggleCart() {
            document.getElementById('cartModal').classList.toggle('active');
        }

        function proceedToCheckout() {
            if (cart.length === 0) {
                alert('Keranjang masih kosong!');
                return;
            }

            document.getElementById('cartModal').classList.remove('active');
            document.getElementById('checkoutModal').classList.add('active');
            updateCheckoutSummary();
        }

        function closeCheckout() {
            document.getElementById('checkoutModal').classList.remove('active');
        }

        function backToCart() {
            document.getElementById('checkoutModal').classList.remove('active');
            document.getElementById('cartModal').classList.add('active');
        }

        function updateShipping() {
            const province = document.getElementById('province').value;
            const shippingCosts = {
                'jawa-barat': 15000,
                'jawa-tengah': 20000,
                'jawa-timur': 25000,
                'dki-jakarta': 10000,
                'banten': 15000,
                'luar-jawa': 50000
            };

            shippingCost = shippingCosts[province] || 15000;
            updateCheckoutSummary();
        }

        function selectPayment(method) {
            selectedPayment = method;
            document.querySelectorAll('.payment-method').forEach(el => el.classList.remove('active'));
            event.target.closest('.payment-method').classList.add('active');
        }

        function updateCheckoutSummary() {
            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const total = subtotal + shippingCost;

            const summaryHTML = `
                <div class="summary-item">
                    <span>Subtotal Produk:</span>
                    <span>Rp ${subtotal.toLocaleString('id-ID')}</span>
                </div>
                <div class="summary-item">
                    <span>Ongkos Kirim:</span>
                    <span>Rp ${shippingCost.toLocaleString('id-ID')}</span>
                </div>
            `;

            document.getElementById('checkoutSummary').innerHTML = summaryHTML;
            document.getElementById('checkoutTotal').textContent = `Rp ${total.toLocaleString('id-ID')}`;
        }

        function completeOrder() {
            const fullName = document.getElementById('fullName').value;
            const phone = document.getElementById('phone').value;
            const province = document.getElementById('province').value;
            const city = document.getElementById('city').value;
            const address = document.getElementById('address').value;

            if (!fullName || !phone || !province || !city || !address) {
                alert('Mohon lengkapi semua data yang wajib diisi!');
                return;
            }

            if (!selectedPayment) {
                alert('Mohon pilih metode pembayaran!');
                return;
            }

            const orderNumber = 'FH' + Date.now().toString().slice(-8);
            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const total = subtotal + shippingCost;

            const paymentNames = {
                'cod': 'Cash on Delivery (COD)',
                'transfer': 'Transfer Bank',
                'ewallet': 'E-Wallet',
                'credit': 'Kartu Kredit'
            };

            const orderItemsHTML = cart.map(item => `
                <div class="order-detail-row">
                    <span>${item.icon} ${item.name} (x${item.quantity})</span>
                    <span>Rp ${(item.price * item.quantity).toLocaleString('id-ID')}</span>
                </div>
            `).join('');

            const district = document.getElementById('district').value;
            const postalCode = document.getElementById('postalCode').value;
            const fullAddress = `${address}, ${city}, ${province.toUpperCase().replace('-', ' ')}${district ? ', ' + district : ''}${postalCode ? ', ' + postalCode : ''}`;

            const orderDetailsHTML = `
                <div style="margin-bottom: 20px;">
                    <strong style="color: #764ba2;">📦 Nomor Pesanan:</strong><br>
                    <span style="font-size: 18px; font-weight: bold;">${orderNumber}</span>
                </div>
                
                <div style="margin-bottom: 15px;">
                    <strong>📍 Pengiriman ke:</strong><br>
                    ${fullName}<br>
                    ${phone}<br>
                    ${fullAddress}
                </div>

                <div style="margin-bottom: 15px;">
                    <strong>💳 Metode Pembayaran:</strong><br>
                    ${paymentNames[selectedPayment]}
                </div>

                <div style="margin-bottom: 15px;">
                    <strong>🛍️ Produk yang Dibeli:</strong>
                    ${orderItemsHTML}
                    <div class="order-detail-row" style="border-top: 2px solid #764ba2; margin-top: 10px; padding-top: 10px;">
                        <span><strong>Subtotal:</strong></span>
                        <span>Rp ${subtotal.toLocaleString('id-ID')}</span>
                    </div>
                    <div class="order-detail-row">
                        <span><strong>Ongkir:</strong></span>
                        <span>Rp ${shippingCost.toLocaleString('id-ID')}</span>
                    </div>
                    <div class="order-detail-row" style="font-size: 18px;">
                        <span><strong>Total:</strong></span>
                        <span style="color: #764ba2;"><strong>Rp ${total.toLocaleString('id-ID')}</strong></span>
                    </div>
                </div>

                ${selectedPayment === 'transfer' ? `
                    <div style="background: #fff3cd; padding: 15px; border-radius: 10px; margin-top: 15px;">
                        <strong>🏦 Informasi Transfer:</strong><br>
                        Bank BCA: 1234567890<br>
                        A/N Fashion Nurul<br><br>
                        <em>Mohon transfer sesuai nominal dan konfirmasi pembayaran melalui WhatsApp.</em>
                    </div>
                ` : ''}

                ${selectedPayment === 'ewallet' ? `
                    <div style="background: #d4edda; padding: 15px; border-radius: 10px; margin-top: 15px;">
                        <strong>📱 E-Wallet:</strong><br>
                        GoPay/OVO/DANA: 081234567890<br>
                        A/N Fashion Nurul<br><br>
                        <em>Scan QRIS atau transfer ke nomor di atas.</em>
                    </div>
                ` : ''}

                ${selectedPayment === 'cod' ? `
                    <div style="background: #d1ecf1; padding: 15px; border-radius: 10px; margin-top: 15px;">
                        <strong>💵 Cash on Delivery:</strong><br>
                        Siapkan uang pas saat barang tiba.<br>
                        Estimasi pengiriman: 2-3 hari kerja.
                    </div>
                ` : ''}

                ${selectedPayment === 'credit' ? `
                    <div style="background: #f8d7da; padding: 15px; border-radius: 10px; margin-top: 15px;">
                        <strong>💳 Kartu Kredit:</strong><br>
                        Link pembayaran akan dikirim via email.<br>
                        Pembayaran dapat dicicil 0% dengan kartu kredit tertentu.
                    </div>
                ` : ''}

                <div style="text-align: center; margin-top: 20px; padding: 15px; background: #e7f3ff; border-radius: 10px;">
                    <p style="margin-bottom: 10px;">📞 <strong>Hubungi Kami:</strong></p>
                    <p>WhatsApp: 0815-4686-0693<br>
                    Email: support@fashionnurul.com</p>
                </div>
            `;

            document.getElementById('orderDetails').innerHTML = orderDetailsHTML;

            document.getElementById('checkoutModal').classList.remove('active');
            document.getElementById('successModal').classList.add('active');

            cart = [];
            selectedPayment = '';
            shippingCost = 0;
            updateCart();
            
            document.getElementById('fullName').value = '';
            document.getElementById('phone').value = '';
            document.getElementById('province').value = '';
            document.getElementById('city').value = '';
            document.getElementById('district').value = '';
            document.getElementById('postalCode').value = '';
            document.getElementById('address').value = '';
            document.querySelectorAll('.payment-method').forEach(el => el.classList.remove('active'));
        }

        function closeSuccess() {
            document.getElementById('successModal').classList.remove('active');
        }

        renderProducts();
    </script>
</body>
</html># Nurul-fashion-online-store
