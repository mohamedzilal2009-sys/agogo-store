# agogo-store
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Boutique En Ligne | Agogo Store</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #2563eb;
            --primary-hover: #1d4ed8;
            --accent: #e11d48;
            --bg: #f8fafc;
            --card-bg: #ffffff;
            --text: #0f172a;
            --text-muted: #64748b;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background-color: var(--bg);
            color: var(--text);
            line-height: 1.6;
        }

        /* En-tête */
        header {
            background: white;
            padding: 1rem 5%;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
            position: sticky;
            top: 0;
            z-index: 100;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.6rem;
            font-weight: 700;
            color: var(--primary);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.03); }
            100% { transform: scale(1); }
        }

        .animate-fade {
            animation: fadeInUp 0.8s ease-out forwards;
        }

        /* Layout Principal */
        .container {
            max-width: 1200px;
            margin: 2.5rem auto;
            padding: 0 1rem;
        }

        .section-header {
            text-align: center;
            margin-bottom: 3rem;
        }

        .section-title {
            font-size: 2rem;
            color: var(--text);
            margin-bottom: 0.5rem;
        }

        .section-subtitle {
            color: var(--text-muted);
            font-size: 1rem;
        }

        /* Grille des Produits */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 2rem;
            align-items: start;
        }

        /* Carte Produit */
        .product-card {
            background: var(--card-bg);
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.05), 0 4px 6px -2px rgba(0, 0, 0, 0.02);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            border: 1px solid #e2e8f0;
        }

        .product-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
        }

        /* Image & Galerie */
        .main-image-container {
            position: relative;
            width: 100%;
            height: 300px;
            background: #f1f5f9;
            overflow: hidden;
        }

        .main-image-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .product-card:hover .main-image-container img {
            transform: scale(1.04);
        }

        .thumbnails {
            display: flex;
            gap: 8px;
            padding: 10px 1rem;
            background: #ffffff;
            border-bottom: 1px solid #f1f5f9;
        }

        .thumb {
            width: 55px;
            height: 55px;
            border-radius: 8px;
            object-fit: cover;
            cursor: pointer;
            border: 2px solid transparent;
            transition: all 0.2s ease;
        }

        .thumb:hover, .thumb.active {
            border-color: var(--primary);
            transform: scale(1.05);
        }

        .product-info {
            padding: 1.5rem;
        }

        .badge {
            background: #dbeafe;
            color: var(--primary);
            padding: 0.25rem 0.75rem;
            border-radius: 50px;
            font-size: 0.75rem;
            font-weight: 600;
            display: inline-block;
            margin-bottom: 0.5rem;
            text-transform: uppercase;
        }

        .price-container {
            display: flex;
            align-items: baseline;
            gap: 10px;
            margin: 0.5rem 0;
        }

        .price-tag {
            font-size: 1.75rem;
            font-weight: 700;
            color: var(--primary);
        }

        .delivery-info {
            font-size: 0.85rem;
            color: #d97706;
            background: #fffbeb;
            padding: 0.4rem 0.75rem;
            border-radius: 8px;
            display: block;
            margin-bottom: 1.2rem;
            border: 1px solid #fef3c7;
            font-weight: 500;
        }

        /* Formulaire de Commande */
        .order-form {
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
            margin-top: 1rem;
            background: #f8fafc;
            padding: 1rem;
            border-radius: 12px;
        }

        .form-control {
            width: 100%;
            padding: 0.75rem 1rem;
            border: 1px solid #cbd5e1;
            border-radius: 8px;
            outline: none;
            font-size: 0.9rem;
            transition: border-color 0.2s ease, box-shadow 0.2s ease;
        }

        .form-control:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }

        .btn-order {
            background: var(--primary);
            color: white;
            border: none;
            padding: 0.85rem;
            border-radius: 8px;
            font-weight: 600;
            font-size: 1rem;
            cursor: pointer;
            transition: background 0.2s ease;
            animation: pulse 2.5s infinite;
        }

        .btn-order:hover {
            background: var(--primary-hover);
        }

        /* Cartes d'attente (Pour ajouter d'autres marchandises) */
        .add-product-card {
            border: 2px dashed #cbd5e1;
            border-radius: 16px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 3rem 1.5rem;
            text-align: center;
            color: var(--text-muted);
            background: rgba(255, 255, 255, 0.6);
            min-height: 500px;
            transition: all 0.3s ease;
        }

        .add-product-card:hover {
            border-color: var(--primary);
            color: var(--primary);
            background: #ffffff;
        }

        .add-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            background: #e2e8f0;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
    </style>
</head>
<body>

    <header>
        <div class="logo">AGOGO STORE</div>
    </header>

    <div class="container animate-fade">
        <div class="section-header">
            <h1 class="section-title">Nos Produits Disponibles</h1>
            <p class="section-subtitle">Commandez en ligne et payez à la livraison partout au Maroc</p>
        </div>

        <div class="products-grid">
            
            <!-- PRODUIT 1 : Lunch Box Électrique (AVEC VOS PHOTOS) -->
            <div class="product-card">
                <div class="main-image-container">
                    <!-- Photo Principale -->
                    <img id="mainImg1" src="Gemini_Generated_Image_591h89591h89591h.jpg" alt="Lunch Box Électrique">
                </div>
                
                <!-- Galerie des 3 photos fournies -->
                <div class="thumbnails">
                    <img src="Gemini_Generated_Image_591h89591h89591h.jpg" class="thumb active" onclick="changeImage('mainImg1', this.src, this)">
                    <img src="34853eed-2c00-4c04-87b0-4dcff619eea4.webp" class="thumb" onclick="changeImage('mainImg1', this.src, this)">
                    <img src="Capture d'écran 2026-08-15 180832.jpg" class="thumb" onclick="changeImage('mainImg1', this.src, this)">
                </div>

                <div class="product-info">
                    <span class="badge">Chauffante & Portative</span>
                    <h3>Lunch Box Électrique Double Étage</h3>
                    <p style="color: var(--text-muted); font-size: 0.88rem; margin-top: 0.3rem;">
                        Chauffez vos repas facilement au bureau ou en voyage. Compartiments Inox séparés de grande capacité.
                    </p>
                    
                    <div class="price-container">
                        <div class="price-tag">250 DH</div>
                    </div>
                    
                    <div class="delivery-info">
                        ⚠️ Livraison non gratuite (Frais ajoutés à la confirmation)
                    </div>

                    <!-- Formulaire de commande rapide -->
                    <form class="order-form" onsubmit="handleOrder(event, 'Lunch Box Électrique')">
                        <input type="text" placeholder="Nom et Prénom" class="form-control" required>
                        <input type="tel" placeholder="Numéro de Téléphone" class="form-control" required>
                        <input type="text" placeholder="Ville de livraison" class="form-control" required>
                        <button type="submit" class="btn-order">Commander Maintenant</button>
                    </form>
                </div>
            </div>

            <!-- EMPLACEMENT RÉSERVÉ N°2 (Espace prêt pour ajouter une marchandise) -->
            <div class="add-product-card">
                <div class="add-icon">📦</div>
                <h3>Emplacement Produit #2</h3>
                <p>Copiez le bloc HTML du premier produit pour ajouter un nouvel article ici.</p>
            </div>

            <!-- EMPLACEMENT RÉSERVÉ N°3 (Espace prêt pour ajouter une marchandise) -->
            <div class="add-product-card">
                <div class="add-icon">➕</div>
                <h3>Emplacement Produit #3</h3>
                <p>Votre boutique est prête à accueillir autant de marchandise que vous souhaitez !</p>
            </div>

        </div>
    </div>

    <script>
        // Fonction pour changer l'image affichée lors du clic sur les vignettes
        function changeImage(targetId, src, element) {
            document.getElementById(targetId).src = src;
            let parent = element.parentElement;
            parent.querySelectorAll('.thumb').forEach(t => t.classList.remove('active'));
            element.classList.add('active');
        }

        // Fonction de traitement de la commande
        function handleOrder(e, productName) {
            e.preventDefault();
            alert('Merci pour votre commande de "' + productName + '" ! Nous vous contacterons par téléphone pour confirmer la livraison.');
        }
    </script>
</body>
</html>
