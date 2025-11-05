<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>M-Pesa Kenya Payment Link Generator</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #00a651 0%, #008c3a 51%, #00732e 100%);
            color: #333;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            background-color: white;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            width: 100%;
            max-width: 500px;
            padding: 30px;
        }
        
        h1 {
            color: #00a651;
            text-align: center;
            margin-bottom: 10px;
            font-size: 28px;
        }
        
        .subtitle {
            text-align: center;
            color: #666;
            margin-bottom: 30px;
            font-size: 16px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #444;
        }
        
        input, select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 16px;
            transition: all 0.3s;
        }
        
        input:focus, select:focus {
            outline: none;
            border-color: #00a651;
            box-shadow: 0 0 0 3px rgba(0, 166, 81, 0.2);
        }
        
        .btn {
            background: linear-gradient(to right, #00a651, #008c3a);
            color: white;
            border: none;
            padding: 14px 20px;
            border-radius: 6px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            width: 100%;
            transition: all 0.3s;
            margin-top: 10px;
        }
        
        .btn:hover {
            background: linear-gradient(to right, #008c3a, #00732e);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .result {
            margin-top: 25px;
            padding: 20px;
            background-color: #f8f9fa;
            border-radius: 6px;
            border-left: 4px solid #00a651;
        }
        
        .result h3 {
            color: #00a651;
            margin-bottom: 10px;
        }
        
        .payment-link {
            word-break: break-all;
            padding: 12px;
            background-color: #e9ecef;
            border-radius: 4px;
            margin: 15px 0;
            font-size: 14px;
        }
        
        .payment-link a {
            color: #00a651;
            text-decoration: none;
            font-weight: 600;
            font-size: 16px;
        }
        
        .payment-link a:hover {
            text-decoration: underline;
        }
        
        .copy-btn {
            background-color: #00a651;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
            margin-right: 10px;
            width: 48%;
        }
        
        .copy-btn:hover {
            background-color: #008c3a;
        }
        
        .test-btn {
            background-color: #ffc107;
            color: #212529;
            border: none;
            padding: 10px 20px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
            width: 48%;
        }
        
        .test-btn:hover {
            background-color: #e0a800;
        }
        
        .button-group {
            display: flex;
            justify-content: space-between;
            margin-top: 15px;
        }
        
        .info-box {
            background-color: #e7f7ef;
            border-radius: 6px;
            padding: 15px;
            margin-top: 25px;
            font-size: 14px;
            color: #00732e;
        }
        
        .info-box h4 {
            margin-bottom: 8px;
            color: #00a651;
        }
        
        .steps {
            margin-top: 15px;
            padding-left: 20px;
        }
        
        .steps li {
            margin-bottom: 8px;
        }
        
        .success-message {
            color: #00a651;
            font-weight: 600;
            text-align: center;
            margin-top: 10px;
            display: none;
        }
        
        .payment-type {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .payment-option {
            flex: 1;
            text-align: center;
            padding: 15px;
            border: 2px solid #ddd;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .payment-option.selected {
            border-color: #00a651;
            background-color: #e7f7ef;
        }
        
        .payment-option h4 {
            color: #00a651;
            margin-bottom: 5px;
        }
        
        @media (max-width: 600px) {
            .container {
                padding: 20px;
            }
            
            h1 {
                font-size: 24px;
            }
            
            .button-group {
                flex-direction: column;
            }
            
            .copy-btn, .test-btn {
                width: 100%;
                margin-bottom: 10px;
            }
            
            .payment-type {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>M-Pesa Kenya Payment Link Generator</h1>
        <p class="subtitle">Create payment links that redirect users to M-Pesa *334# menu</p>
        
        <div class="payment-type">
            <div class="payment-option selected" id="paybillOption">
                <h4>Pay Business</h4>
                <p>Paybill Number</p>
            </div>
            <div class="payment-option" id="tillOption">
                <h4>Buy Goods</h4>
                <p>Till Number</p>
            </div>
            <div class="payment-option" id="sendMoneyOption">
                <h4>Send Money</h4>
                <p>Phone Number</p>
            </div>
        </div>
        
        <form id="paymentForm">
            <div class="form-group">
                <label for="recipient">Recipient Number</label>
                <input type="text" id="recipient" placeholder="e.g., 9081999 or 0712345678" value="9081999" required>
            </div>
            
            <div class="form-group">
                <label for="amount">Amount (KES)</label>
                <input type="number" id="amount" placeholder="e.g., 100" min="1" value="100" required>
            </div>
            
            <div class="form-group">
                <label for="reference">Payment Reference</label>
                <input type="text" id="reference" placeholder="e.g., Order #12345" value="Test Payment" required>
            </div>
            
            <button type="submit" class="btn">Generate M-Pesa Payment Link</button>
        </form>
        
        <div class="result" id="result">
            <h3>Your M-Pesa Payment Link is Ready!</h3>
            <p>Share this link with your customer to receive payment:</p>
            <div class="payment-link">
                <strong>USSD Code:</strong> <span id="ussdCode">*334*1*1*9081999*100*Test Payment#</span><br><br>
                <strong>Payment Link:</strong> <a href="tel:*334*1*1*9081999*100*Test Payment#" id="generatedLink">Click to Pay with M-Pesa</a>
            </div>
            <div class="button-group">
                <button class="copy-btn" id="copyBtn">Copy Link</button>
                <button class="test-btn" id="testBtn">Test Link</button>
            </div>
            <div class="success-message" id="successMessage">Link copied to clipboard!</div>
        </div>
        
        <div class="info-box">
            <h4>How It Works - M-Pesa Kenya (*334#)</h4>
            <p>This generator creates a custom link that redirects users to initiate an M-Pesa payment via the official *334# USSD code.</p>
            
            <h4>Steps for Customer:</h4>
            <ol class="steps">
                <li>Click the payment link on their phone</li>
                <li>Phone dialer opens with USSD code pre-filled</li>
                <li>They press "Call" or "Send" to open M-Pesa</li>
                <li>They enter M-Pesa PIN to complete payment</li>
                <li>Payment is processed instantly</li>
            </ol>
            
            <p><strong>Format:</strong> <code>tel:*334*1*1*Paybill*Amount*Reference#</code></p>
            <p><strong>Note:</strong> This uses the official M-Pesa Kenya USSD code *334# and works on all phones.</p>
        </div>
    </div>

    <script>
        let paymentType = 'paybill'; // Default to Paybill
        
        // Payment type selection
        document.getElementById('paybillOption').addEventListener('click', function() {
            paymentType = 'paybill';
            updatePaymentType();
            updatePlaceholder();
        });
        
        document.getElementById('tillOption').addEventListener('click', function() {
            paymentType = 'till';
            updatePaymentType();
            updatePlaceholder();
        });
        
        document.getElementById('sendMoneyOption').addEventListener('click', function() {
            paymentType = 'sendMoney';
            updatePaymentType();
            updatePlaceholder();
        });
        
        function updatePaymentType() {
            // Remove selected class from all
            document.querySelectorAll('.payment-option').forEach(option => {
                option.classList.remove('selected');
            });
            
            // Add selected class to current
            document.getElementById(paymentType + 'Option').classList.add('selected');
        }
        
        function updatePlaceholder() {
            const recipientInput = document.getElementById('recipient');
            if (paymentType === 'sendMoney') {
                recipientInput.placeholder = 'e.g., 0712345678';
                recipientInput.value = '0712345678';
            } else {
                recipientInput.placeholder = 'e.g., 9081999';
                recipientInput.value = '9081999';
            }
        }
        
        document.getElementById('paymentForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const recipient = document.getElementById('recipient').value;
            const amount = document.getElementById('amount').value;
            const reference = document.getElementById('reference').value;
            
            let ussdCode;
            
            if (paymentType === 'sendMoney') {
                // Send Money format: *334*1*1*Phone*Amount*Reference#
                ussdCode = `*334*1*1*${recipient}*${amount}*${reference}#`;
            } else {
                // Paybill/Till format: *334*1*1*Number*Amount*Reference#
                ussdCode = `*334*1*1*${recipient}*${amount}*${reference}#`;
            }
            
            const paymentLink = `tel:${ussdCode}`;
            
            // Update the display
            document.getElementById('ussdCode').textContent = ussdCode;
            const generatedLink = document.getElementById('generatedLink');
            generatedLink.href = paymentLink;
            generatedLink.textContent = 'Click to Pay with M-Pesa Kenya';
            
            document.getElementById('result').style.display = 'block';
        });
        
        document.getElementById('copyBtn').addEventListener('click', function() {
            const link = document.getElementById('generatedLink').href;
            
            // Create a temporary input to copy the link
            const tempInput = document.createElement('input');
            tempInput.value = link;
            document.body.appendChild(tempInput);
            tempInput.select();
            document.execCommand('copy');
            document.body.removeChild(tempInput);
            
            // Show success message
            const successMessage = document.getElementById('successMessage');
            successMessage.style.display = 'block';
            setTimeout(() => {
                successMessage.style.display = 'none';
            }, 2000);
        });
        
        document.getElementById('testBtn').addEventListener('click', function() {
            const paymentLink = document.getElementById('generatedLink').href;
            window.location.href = paymentLink;
        });
        
        // Initialize
        updatePlaceholder();
    </script>
</body>
</html>
