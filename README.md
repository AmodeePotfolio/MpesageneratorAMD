
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pay with M-Pesa Kenya</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), 
                        url('https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            color: white;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
            width: 100%;
            max-width: 450px;
            padding: 40px 30px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.2);
            animation: fadeInUp 1s ease-out;
        }
        
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .logo {
            width: 80px;
            height: 80px;
            background: #00a651;
            border-radius: 50%;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 40px;
            font-weight: bold;
            animation: bounce 2s infinite;
            box-shadow: 0 10px 30px rgba(0, 166, 81, 0.4);
        }
        
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateY(0);
            }
            40% {
                transform: translateY(-10px);
            }
            60% {
                transform: translateY(-5px);
            }
        }
        
        h1 {
            font-size: 32px;
            margin-bottom: 10px;
            background: linear-gradient(45deg, #00a651, #80d4aa);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: glow 2s ease-in-out infinite alternate;
        }
        
        @keyframes glow {
            from {
                text-shadow: 0 0 10px rgba(0, 166, 81, 0.5);
            }
            to {
                text-shadow: 0 0 20px rgba(0, 166, 81, 0.8), 0 0 30px rgba(0, 166, 81, 0.6);
            }
        }
        
        .subtitle {
            color: #ccc;
            margin-bottom: 30px;
            font-size: 16px;
            animation: fadeIn 2s ease-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .payment-card {
            background: rgba(255, 255, 255, 0.15);
            border-radius: 15px;
            padding: 25px;
            margin: 25px 0;
            border: 1px solid rgba(255, 255, 255, 0.1);
            animation: slideInLeft 1s ease-out;
        }
        
        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }
        
        .amount {
            font-size: 48px;
            font-weight: bold;
            color: #00a651;
            margin: 15px 0;
            text-shadow: 0 5px 15px rgba(0, 166, 81, 0.3);
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        .details {
            text-align: left;
            margin: 20px 0;
        }
        
        .detail-item {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            animation: fadeIn 1s ease-out;
        }
        
        .detail-item:last-child {
            border-bottom: none;
        }
        
        .pay-btn {
            background: linear-gradient(45deg, #00a651, #008c3a);
            color: white;
            border: none;
            padding: 18px 40px;
            border-radius: 50px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            transition: all 0.3s ease;
            margin: 20px 0;
            box-shadow: 0 10px 30px rgba(0, 166, 81, 0.4);
            position: relative;
            overflow: hidden;
            animation: slideInRight 1s ease-out;
        }
        
        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }
        
        .pay-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(0, 166, 81, 0.6);
            background: linear-gradient(45deg, #008c3a, #00732e);
        }
        
        .pay-btn:active {
            transform: translateY(0);
        }
        
        .pay-btn::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: 0.5s;
        }
        
        .pay-btn:hover::after {
            left: 100%;
        }
        
        .instructions {
            background: rgba(0, 166, 81, 0.2);
            border-radius: 10px;
            padding: 20px;
            margin-top: 25px;
            border-left: 4px solid #00a651;
            animation: fadeIn 1.5s ease-out;
        }
        
        .instructions h3 {
            color: #80d4aa;
            margin-bottom: 10px;
            font-size: 16px;
        }
        
        .steps {
            text-align: left;
            font-size: 14px;
            color: #ccc;
        }
        
        .steps li {
            margin-bottom: 8px;
            padding-left: 5px;
        }
        
        .loading {
            display: none;
            margin: 20px 0;
        }
        
        .loader {
            width: 40px;
            height: 40px;
            border: 4px solid rgba(255,255,255,0.3);
            border-top: 4px solid #00a651;
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 0 auto;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .countdown {
            font-size: 14px;
            color: #80d4aa;
            margin-top: 10px;
        }
        
        .floating {
            animation: floating 3s ease-in-out infinite;
        }
        
        @keyframes floating {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }
        
        @media (max-width: 480px) {
            .container {
                padding: 30px 20px;
                margin: 10px;
            }
            
            h1 {
                font-size: 28px;
            }
            
            .amount {
                font-size: 36px;
            }
            
            .pay-btn {
                padding: 16px 30px;
                font-size: 16px;
            }
        }
    </style>
</head>
<body>
    <div class="container floating">
        <div class="logo">M</div>
        <h1>Pay with M-Pesa</h1>
        <p class="subtitle">Secure & Instant Payment</p>
        
        <div class="payment-card">
            <div class="amount">KES 500-50K</div>
            <div class="details">
                <div class="detail-item" style="animation-delay: 0.2s">
                    <span>Business:</span>
                    <span>CHARTERED INVESTMENTS</span>
                </div>
                <div class="detail-item" style="animation-delay: 0.4s">
                    <span>Paybill:</span>
                    <span>9081999</span>
                </div>
                <div class="detail-item" style="animation-delay: 0.6s">
                    <span>Account:</span>
                    <span>ORDER123</span>
                </div>
            </div>
        </div>
        
        <button class="pay-btn" id="payButton">
            💰 PAY NOW
        </button>
        
        <div class="loading" id="loading">
            <div class="loader"></div>
            <div class="countdown" id="countdown">Redirecting in 3 seconds...</div>
        </div>
        
        <div class="instructions">
            <h3>📱 Payment Instructions</h3>
            <ul class="steps">
                <li>Click "PAY NOW" button above</li>
                <li>Your phone will open M-Pesa USSD menu</li>
                <li>Follow the prompts to complete payment</li>
                <li>Enter your M-Pesa PIN when prompted</li>
                <li>You'll receive confirmation via SMS</li>
            </ul>
        </div>
    </div>

    <script>
        document.getElementById('payButton').addEventListener('click', function() {
            const button = this;
            const loading = document.getElementById('loading');
            const countdown = document.getElementById('countdown');
            
            // Show loading animation
            button.style.display = 'none';
            loading.style.display = 'block';
            
            // Countdown animation
            let seconds = 3;
            const countdownInterval = setInterval(() => {
                countdown.textContent = `Redirecting in ${seconds} seconds...`;
                seconds--;
                
                if (seconds < 0) {
                    clearInterval(countdownInterval);
                    // Redirect to M-Pesa USSD
                    window.location.href = 'tel:*334%23';
                }
            }, 1000);
            
            // Fallback: If redirect doesn't work, show instructions
            setTimeout(() => {
                if (!document.hidden) {
                    loading.innerHTML = '<div style="color: #80d4aa;">📞 Please dial *334# manually on your phone</div>';
                }
            }, 5000);
        });
        
        // Add some interactive effects
        document.addEventListener('mousemove', (e) => {
            const container = document.querySelector('.container');
            const xAxis = (window.innerWidth / 2 - e.pageX) / 25;
            const yAxis = (window.innerHeight / 2 - e.pageY) / 25;
            container.style.transform = `rotateY(${xAxis}deg) rotateX(${yAxis}deg)`;
        });
        
        // Reset transform when mouse leaves
        document.querySelector('.container').addEventListener('mouseleave', (e) => {
            e.target.style.transform = 'rotateY(0deg) rotateX(0deg)';
            e.target.style.transition = 'transform 0.5s ease';
        });
        
        // Add entrance animation to elements
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animationPlayState = 'running';
                }
            });
        });
        
        // Observe all animated elements
        document.querySelectorAll('.container, .payment-card, .pay-btn, .instructions').forEach(el => {
            observer.observe(el);
        });
    </script>
</body>
</html>
