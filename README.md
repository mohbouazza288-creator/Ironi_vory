<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Iron & Ivory - Premium Shop</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
    <script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>

    <style>
        :root { --gold: #c5a059; --dark: #050a0f; --card: #111b25; --white: #ffffff; }
        body { background-color: var(--dark); color: var(--white); font-family: 'Cairo', sans-serif; margin: 0; padding-top: 40px; overflow-x: hidden; }

        .announcement-bar { background-color: var(--gold); color: black; text-align: center; padding: 8px 0; font-size: 14px; font-weight: bold; position: fixed; top: 0; width: 100%; z-index: 1000; }
        .page { display: none; min-height: 100vh; animation: fadeIn 0.5s ease; }
        .page.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        header { height: 35vh; background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.7)), url('https://iafevewyaewiujdxipil.supabase.co/storage/v1/object/public/assets/1774290915307.jpg'); background-size: cover; background-position: center; display: flex; flex-direction: column; align-items: center; justify-content: center; text-align: center; }
        
        .bio-section { padding: 25px 15px; text-align: center; background: rgba(197, 160, 89, 0.05); border-bottom: 1px solid rgba(197, 160, 89, 0.2); }
        .bio-section h2 { color: var(--gold); font-size: 20px; margin-bottom: 8px; }
        .bio-section p { font-size: 14px; line-height: 1.6; max-width: 500px; margin: 0 auto; opacity: 0.8; }

        .container { max-width: 600px; margin: 20px auto 50px; padding: 15px; }
        .product-card { background: var(--card); border-radius: 20px; overflow: hidden; border: 1px solid rgba(197, 160, 89, 0.2); margin-bottom: 30px; box-shadow: 0 10px 20px rgba(0,0,0,0.3); }
        
        /* تنسيق سلايدر الصور */
        .swiper { width: 100%; height: 380px; }
        .swiper-slide img { width: 100%; height: 100%; object-fit: cover; cursor: pointer; }
        .swiper-pagination-bullet-active { background: var(--gold); }

        .details { padding: 20px; text-align: center; }
        .product-desc { font-size: 14px; opacity: 0.7; line-height: 1.6; margin: 10px 0 15px; text-align: justify; padding: 0 10px; }
        .price { color: var(--gold); font-size: 26px; font-weight: bold; display: block; margin: 10px 0; }
        .buy-btn { background: var(--gold); color: black; border: none; padding: 14px; border-radius: 30px; font-weight: bold; cursor: pointer; width: 100%; font-size: 18px; transition: 0.3s; }

        .checkout-box { padding: 20px; text-align: center; }
        input, select { width: 100%; padding: 14px; margin: 10px 0; border-radius: 10px; border: 1px solid #2a3a4a; background: #0a1118; color: white; font-family: 'Cairo'; box-sizing: border-box; font-size: 16px; }
        
        .delivery-options { display: flex; gap: 10px; margin: 15px 0; }
        .delivery-options label { flex: 1; background: #0a1118; border: 1px solid #2a3a4a; padding: 12px; border-radius: 10px; cursor: pointer; transition: 0.3s; }
        .delivery-options input[type="radio"]:checked + span { color: var(--gold); font-weight: bold; }
        
        .total-box { background: rgba(197, 160, 89, 0.1); padding: 15px; border-radius: 10px; margin: 20px 0; border: 1px dashed var(--gold); }
        
        /* نافذة تكبير الصور Lightbox */
        .lightbox { display: none; position: fixed; z-index: 3000; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.95); align-items: center; justify-content: center; }
        .lightbox img { max-width: 95%; max-height: 90%; border: 1px solid var(--gold); border-radius: 10px; }

        .social-bar { display: flex; justify-content: center; gap: 30px; padding: 30px; background: rgba(255,255,255,0.03); }
        .social-bar a { color: var(--white); font-size: 28px; transition: 0.3s; }
        footer { text-align: center; padding: 20px; font-size: 10px; opacity: 0.4; }
    </style>
</head>
<body>

    <div class="announcement-bar">🚚 التوصيل متوفر لـ 58 ولاية - الدفع عند الاستلام</div>

    <div id="lightbox" class="lightbox" onclick="this.style.display='none'">
        <img id="lightboxImg" src="">
    </div>

    <div id="shopPage" class="page active">
        <header>
            <h1 style="color: var(--gold); margin: 0; font-size: 32px;">Iron & Ivory</h1>
            <p>Luxury & Excellence</p>
        </header>

        <section class="bio-section">
            <h2>فخامة في كل ثانية</h2>
            <p>وجهتكم الأولى في الجزائر لأفخم الساعات العالمية المختارة بعناية. نجمع بين الجودة العالية والتصميم العصري لنقدم لكم الأفضل دائماً.</p>
        </section>

        <div class="container" id="productsContainer">
            <div style="text-align: center; padding: 50px;">جاري تحميل التشكيلة الفاخرة...</div>
        </div>
        <div class="social-bar">
            <a href="https://www.facebook.com/profile.php?id=61588316577510" target="_blank"><i class="fab fa-facebook"></i></a>
            <a href="https://www.instagram.com/ironi_vory" target="_blank"><i class="fab fa-instagram"></i></a>
            <a href="https://www.tiktok.com/@iron.ivory.timepi" target="_blank"><i class="fab fa-tiktok"></i></a>
        </div>
        <footer>POWERED BY DEVNODE DZ</footer>
    </div>

    <div id="checkoutPage" class="page">
        <div class="checkout-box">
            <div onclick="showPage('shopPage')" style="color: var(--gold); cursor: pointer; margin-bottom: 20px; font-weight: bold;"><i class="fas fa-arrow-right"></i> العودة للمتجر</div>
            <h2 id="orderTitle" style="color: var(--gold);"></h2>
            <img id="orderImg" style="width: 150px; border-radius: 15px; margin-bottom: 15px; border: 1px solid var(--gold);">
            
            <form onsubmit="sendOrder(event)">
                <input type="text" id="userName" placeholder="الاسم الكامل" required>
                <input type="tel" id="userPhone" placeholder="رقم الهاتف (مثال: 06XXXXXXXX)" pattern="^(05|06|07)[0-9]{8}$" maxlength="10" required>
                <select id="userWilaya" onchange="updateTotal()" required>
                    <option value="">اختر الولاية</option>
                </select>

                <div class="delivery-options">
                    <label><input type="radio" name="delType" value="home" checked onclick="updateTotal()"> <span>🏠 للمنزل</span></label>
                    <label><input type="radio" name="delType" value="office" onclick="updateTotal()"> <span>🏢 للمكتب</span></label>
                </div>

                <div class="total-box">
                    <div>سعر الساعة: <span id="itemPrice">0</span> دج</div>
                    <div>سعر التوصيل: <span id="deliveryPrice">0</span> دج</div>
                    <hr style="border: 0.5px solid rgba(197,160,89,0.3)">
                    <div style="font-size: 20px; font-weight: bold; color: var(--gold);">الإجمالي: <span id="finalTotal">0</span> دج</div>
                </div>

                <button type="submit" id="submitBtn" class="buy-btn">تأكيد الطلبية</button>
            </form>
        </div>
    </div>

    <div id="successPage" class="page">
        <div style="text-align:center; padding: 100px 20px;">
            <i class="fas fa-check-circle" style="font-size: 70px; color: #2ecc71; margin-bottom: 20px;"></i>
            <h2>تم الطلب بنجاح!</h2>
            <p>سنتصل بك هاتفياً قريباً لتأكيد طلبك.</p>
            <button class="buy-btn" onclick="showPage('shopPage')" style="max-width: 250px;">العودة للمتجر</button>
        </div>
    </div>

    <script>
        const SHEETY_API = "https://api.sheety.co/877a195886dba5c922cc88f09c889f32/omar/feuille1";
        const BOT_TOKEN = "8422539267:AAEkuMplvIbLWF_Q8ogjUE1Q4in1euemxvM";
        const CHAT_ID = "8332065634";

        const shippingData = {"01 أدرار": [1500, 1000], "02 الشلف": [750, 450], "03 الأغواط": [1000, 600], "04 أم البواقي": [900, 600], "05 باتنة": [900, 600], "06 بجاية": [800, 500], "07 بسكرة": [1100, 700], "08 بشار": [1200, 800], "09 البليدة": [750, 450], "10 البويرة": [800, 500], "11 تمنراست": [2000, 1500], "12 تبسة": [900, 600], "13 تلمسان": [800, 500], "14 تيارت": [800, 500], "15 تيزي وزو": [800, 500], "16 الجزائر": [700, 450], "17 الجلفة": [1000, 600], "18 جيجل": [900, 600], "19 سطيف": [900, 600], "20 سعيدة": [500, 300], "21 سكيكدة": [900, 600], "22 سيدي بلعباس": [650, 400], "23 عنابة": [900, 600], "24 قالمة": [900, 600], "25 قسنطينة": [900, 600], "26 المدية": [900, 600], "27 مستغانم": [800, 500], "28 المسيلة": [900, 600], "29 معسكر": [600, 400], "30 ورقلة": [1000, 600], "31 وهران": [700, 450], "32 البيض": [1200, 800], "33 إليزي": [1900, 1500], "34 برج بوعريريج": [900, 600], "35 بومرداس": [750, 450], "36 الطارف": [900, 600], "37 تندوف": [1700, 1000], "38 تيسمسيلت": [900, 600], "39 الوادي": [1000, 600], "40 خنشلة": [900, 600], "41 سوق أهراس": [900, 600], "42 تيبازة": [750, 450], "43 ميلة": [900, 600], "44 عين الدفلى": [800, 500], "45 النعامة": [1200, 800], "46 عين تموشنت": [800, 500], "47 غرداية": [1000, 600], "48 غليزان": [700, 450], "49 أولاد جلال": [1100, 700], "50 بني عباس": [1200, 800], "51 إن صالح": [1800, 1200], "52 إن قزام": [2200, 1800], "53 تقرت": [1000, 600], "54 جانت": [2200, 1800], "55 المغير": [1000, 600], "56 المنيعة": [1000, 600], "58 برج باجي مختار": [2000, 1500]};

        let currentPrice = 0;
        let selectedTitle = "";

        function showPage(id) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            document.getElementById(id).classList.add('active');
            window.scrollTo(0,0);
        }

        async function getProducts() {
            try {
                const response = await fetch(SHEETY_API);
                const data = await response.json();
                const container = document.getElementById('productsContainer');
                container.innerHTML = "";
                data.feuille1.forEach((item, index) => {
                    // تجميع الصور (يتوقع وجود أعمدة image, image2, image3, image4 في Sheety)
                    const images = [item.image, item.image2, item.image3, item.image4].filter(img => img);
                    let slides = images.map(img => `<div class="swiper-slide"><img src="${img}" onclick="zoomImg('${img}')"></div>`).join('');

                    container.innerHTML += `
                    <div class="product-card">
                        <div class="swiper swiper-${index}">
                            <div class="swiper-wrapper">${slides}</div>
                            <div class="swiper-pagination"></div>
                        </div>
                        <div class="details">
                            <h3>${item.title}</h3>
                            <p class="product-desc">${item.description || 'فخامة وتميز في التصميم.'}</p>
                            <span class="price">${item.price} دج</span>
                            <button class="buy-btn" onclick="openOrder('${item.title}', '${item.image}', '${item.price}')">اطلب الآن</button>
                        </div>
                    </div>`;
                    
                    // تفعيل اللمس لكل سلايدر بعد إضافته
                    setTimeout(() => {
                        new Swiper(`.swiper-${index}`, {
                            pagination: { el: '.swiper-pagination', clickable: true },
                            grabCursor: true
                        });
                    }, 100);
                });
            } catch (e) { console.error(e); }
        }

        function zoomImg(src) {
            document.getElementById('lightboxImg').src = src;
            document.getElementById('lightbox').style.display = 'flex';
        }

        function openOrder(title, img, price) {
            selectedTitle = title;
            currentPrice = parseInt(price.toString().replace(/[^0-9]/g, ''));
            document.getElementById('orderTitle').innerText = title;
            document.getElementById('orderImg').src = img;
            document.getElementById('itemPrice').innerText = currentPrice;
            showPage('checkoutPage');
            updateTotal();
        }

        function updateTotal() {
            const wilaya = document.getElementById('userWilaya').value;
            const type = document.querySelector('input[name="delType"]:checked').value;
            let delCost = 0;
            if (wilaya && shippingData[wilaya]) {
                delCost = (type === 'home') ? shippingData[wilaya][0] : shippingData[wilaya][1];
            }
            document.getElementById('deliveryPrice').innerText = delCost;
            document.getElementById('finalTotal').innerText = currentPrice + delCost;
        }

        async function sendOrder(e) {
            e.preventDefault();
            const btn = document.getElementById('submitBtn');
            const name = document.getElementById('userName').value;
            const phone = document.getElementById('userPhone').value;
            const wilaya = document.getElementById('userWilaya').value;
            const type = document.querySelector('input[name="delType"]:checked').value === 'home' ? "🏠 للمنزل" : "🏢 للمكتب";
            const total = document.getElementById('finalTotal').innerText;

            btn.disabled = true;
            btn.innerText = "جاري الإرسال...";

            const text = `📦 طلب جديد من الموقع!\n\n⌚ المنتج: ${selectedTitle}\n👤 الاسم: ${name}\n📞 الهاتف: ${phone}\n📍 الولاية: ${wilaya}\n🚚 التوصيل: ${type}\n💰 الإجمالي: ${total} دج`;

            try {
                await fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({ chat_id: CHAT_ID, text: text })
                });
                showPage('successPage');
                e.target.reset();
            } catch (err) { alert("❌ فشل الاتصال، حاول مرة أخرى."); }
            finally { btn.disabled = false; btn.innerText = "تأكيد الطلبية"; }
        }

        const wilayaSelect = document.getElementById('userWilaya');
        Object.keys(shippingData).forEach(w => {
            let opt = document.createElement('option');
            opt.value = w; opt.innerHTML = w;
            wilayaSelect.appendChild(opt);
        });

        getProducts();
    </script>
</body>
</html>
