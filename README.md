<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Device & Browser Information</title>
    <meta name="description" content="Comprehensive device and browser information with modern interface">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
            color: #333;
            overflow-x: hidden;
        }

        .animated-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border-radius: 24px;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.15);
            border: 1px solid rgba(255, 255, 255, 0.2);
            overflow: hidden;
            animation: slideIn 0.8s ease-out;
        }

        @keyframes slideIn {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .header {
            background: linear-gradient(135deg, #667eea, #764ba2);
            padding: 40px 30px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
            animation: rotate 20s linear infinite;
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        h1 {
            font-size: 3rem;
            font-weight: 700;
            color: white;
            margin-bottom: 10px;
            text-shadow: 0 4px 8px rgba(0,0,0,0.3);
            position: relative;
            z-index: 1;
        }

        .subtitle {
            color: rgba(255, 255, 255, 0.9);
            font-size: 1.2rem;
            font-weight: 300;
            position: relative;
            z-index: 1;
        }

        .content {
            padding: 40px 30px;
        }

        .info-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        .info-card {
            background: linear-gradient(145deg, #f8f9ff, #e8eeff);
            border-radius: 16px;
            padding: 25px;
            border: 1px solid rgba(102, 126, 234, 0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .info-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            transition: left 0.5s;
        }

        .info-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(102, 126, 234, 0.15);
        }

        .info-card:hover::before {
            left: 100%;
        }

        .card-title {
            font-size: 1.1rem;
            font-weight: 600;
            color: #667eea;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .card-icon {
            width: 24px;
            height: 24px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border-radius: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 12px;
        }

        .info-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 12px 0;
            border-bottom: 1px solid rgba(102, 126, 234, 0.1);
        }

        .info-item:last-child {
            border-bottom: none;
        }

        .info-label {
            font-weight: 500;
            color: #5a6c7d;
        }

        .info-value {
            font-weight: 600;
            color: #2d3748;
            text-align: right;
            max-width: 60%;
            word-break: break-word;
        }

        .user-agent-section {
            background: linear-gradient(145deg, #2d3748, #1a202c);
            border-radius: 16px;
            padding: 25px;
            margin-top: 30px;
            position: relative;
            overflow: hidden;
        }

        .user-agent-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, #667eea, #764ba2, #667eea);
            background-size: 200% 100%;
            animation: shimmer 2s linear infinite;
        }

        @keyframes shimmer {
            0% { background-position: -200% 0; }
            100% { background-position: 200% 0; }
        }

        .user-agent-title {
            color: white;
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .user-agent-content {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 12px;
            padding: 20px;
            font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
            font-size: 13px;
            line-height: 1.6;
            color: #e2e8f0;
            word-break: break-all;
            border: 1px solid rgba(255, 255, 255, 0.1);
            position: relative;
        }

        .action-buttons {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin-top: 20px;
            flex-wrap: wrap;
        }

        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: 50px;
            font-weight: 600;
            font-size: 14px;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            min-width: 140px;
        }

        .btn-primary {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            box-shadow: 0 8px 16px rgba(102, 126, 234, 0.3);
        }

        .btn-secondary {
            background: linear-gradient(135deg, #f093fb, #f5576c);
            color: white;
            box-shadow: 0 8px 16px rgba(245, 87, 108, 0.3);
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 12px 24px rgba(0, 0, 0, 0.2);
        }

        .btn:active {
            transform: translateY(0);
        }

        .status-indicator {
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .status-dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            animation: pulse 2s infinite;
        }

        .online {
            background-color: #48bb78;
        }

        .offline {
            background-color: #f56565;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        .refresh-btn {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border: none;
            cursor: pointer;
            box-shadow: 0 8px 20px rgba(102, 126, 234, 0.4);
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
        }

        .refresh-btn:hover {
            transform: scale(1.1) rotate(180deg);
        }

        .toast {
            position: fixed;
            top: 20px;
            right: 20px;
            background: linear-gradient(135deg, #48bb78, #38a169);
            color: white;
            padding: 16px 24px;
            border-radius: 12px;
            box-shadow: 0 8px 20px rgba(72, 187, 120, 0.3);
            transform: translateX(400px);
            transition: transform 0.3s ease;
            z-index: 1000;
            font-weight: 500;
        }

        .toast.show {
            transform: translateX(0);
        }

        @media (max-width: 768px) {
            .container {
                margin: 10px;
                border-radius: 16px;
            }
            
            h1 {
                font-size: 2rem;
            }
            
            .info-grid {
                grid-template-columns: 1fr;
            }
            
            .action-buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .btn {
                width: 100%;
                max-width: 300px;
            }
        }
    </style>
</head>
<body>
    <div class="animated-bg"></div>
    
    <div class="container">
        <div class="header">
            <h1>Device & Browser Info</h1>
            <p class="subtitle">Comprehensive system and browser analytics</p>
        </div>

        <div class="content">
            <div class="info-grid">
                <div class="info-card">
                    <div class="card-title">
                        <div class="card-icon">🌐</div>
                        Browser Information
                    </div>
                    <div class="info-item">
                        <span class="info-label">Browser</span>
                        <span class="info-value" id="browserName">-</span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Version</span>
                        <span class="info-value" id="browserVersion">-</span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Engine</span>
                        <span class="info-value" id="browserEngine">-</span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Cookies</span>
                        <span class="info-value" id="cookiesEnabled">-</span>
                    </div>
                </div>

                <div class="info-card">
                    <div class="card-title">
                        <div class="card-icon">💻</div>
                        System Information
                    </div>
                    <div class="info-item">
                        <span class="info-label">Operating System</span>
                        <span class="info-value" id="os">-</span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Platform</span>
                        <span class="info-value" id="platform">-</span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Architecture</span>
                        <span class="info-value" id="architecture">-</span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">CPU Cores</span>
                        <span class="info-value" id="cpuCores">-</span>
                    </div>
                </div>

                <div class="info-card">
                    <div class="card-title">
                        <div class="card-icon">📱</div>
                        Display Information
                    </div>
                    <div class="info-item">
                        <span class="info-label">Screen Resolution</span>
                        <span class="info-value" id="screenResolution">-</span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Viewport Size</span>
                        <span class="info-value" id="viewportSize">-</span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Pixel Ratio</span>
                        <span class="info-value" id="pixelRatio">-</span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Color Depth</span>
                        <span class="info-value" id="colorDepth">-</span>
                    </div>
                </div>

                <div class="info-card">
                    <div class="card-title">
                        <div class="card-icon">🌍</div>
                        Network & Location
                    </div>
                    <div class="info-item">
                        <span class="info-label">Connection</span>
                        <span class="info-value status-indicator" id="onlineStatus">
                            <span class="status-dot online"></span>
                            Online
                        </span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Language</span>
                        <span class="info-value" id="language">-</span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Timezone</span>
                        <span class="info-value" id="timezone">-</span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Touch Support</span>
                        <span class="info-value" id="touchSupport">-</span>
                    </div>
                </div>
            </div>

            <div class="user-agent-section">
                <div class="user-agent-title">
                    <div class="card-icon">🔍</div>
                    User Agent String
                </div>
                <div class="user-agent-content" id="userAgentString">
                    Loading...
                </div>
                <div class="action-buttons">
                    <button class="btn btn-primary" onclick="copyUserAgent()">📋 Copy User Agent</button>
                    <button class="btn btn-secondary" onclick="exportData()">💾 Export Data</button>
                </div>
            </div>
        </div>
    </div>

    <button class="refresh-btn" onclick="refreshData()" title="Refresh Data">
        🔄
    </button>

    <div class="toast" id="toast"></div>

    <script>
        let deviceData = {};

        function showToast(message) {
            const toast = document.getElementById('toast');
            toast.textContent = message;
            toast.classList.add('show');
            setTimeout(() => {
                toast.classList.remove('show');
            }, 3000);
        }

        function getDetailedBrowserInfo() {
            const ua = navigator.userAgent;
            let browserName = "Unknown Browser";
            let browserVersion = "Unknown";
            let browserEngine = "Unknown";

            // Enhanced browser detection
            if (/Opera|OPR/.test(ua)) {
                browserName = "Opera";
                const match = ua.match(/(Opera|OPR)\/([\d.]+)/);
                if (match) browserVersion = match[2];
                browserEngine = "Blink";
            } else if (/Edg/.test(ua)) {
                browserName = "Microsoft Edge";
                const match = ua.match(/Edg\/([\d.]+)/);
                if (match) browserVersion = match[1];
                browserEngine = "Blink";
            } else if (/Chrome/.test(ua) && !/Chromium/.test(ua)) {
                browserName = "Google Chrome";
                const match = ua.match(/Chrome\/([\d.]+)/);
                if (match) browserVersion = match[1];
                browserEngine = "Blink";
            } else if (/Safari/.test(ua) && !/Chrome/.test(ua)) {
                browserName = "Safari";
                const match = ua.match(/Version\/([\d.]+)/);
                if (match) browserVersion = match[1];
                browserEngine = "WebKit";
            } else if (/Firefox/.test(ua)) {
                browserName = "Mozilla Firefox";
                const match = ua.match(/Firefox\/([\d.]+)/);
                if (match) browserVersion = match[1];
                browserEngine = "Gecko";
            }

            return { name: browserName, version: browserVersion, engine: browserEngine };
        }

        function getDetailedOS() {
            const ua = navigator.userAgent;
            
            if (/Windows NT 10/.test(ua)) return "Windows 10/11";
            if (/Windows NT 6.3/.test(ua)) return "Windows 8.1";
            if (/Windows NT 6.2/.test(ua)) return "Windows 8";
            if (/Windows NT 6.1/.test(ua)) return "Windows 7";
            if (/Windows/.test(ua)) return "Windows";
            
            if (/iPhone/.test(ua)) return "iOS (iPhone)";
            if (/iPad/.test(ua)) return "iOS (iPad)";
            if (/iPod/.test(ua)) return "iOS (iPod)";
            
            if (/Android/.test(ua)) {
                const match = ua.match(/Android ([\d.]+)/);
                return match ? `Android ${match[1]}` : "Android";
            }
            
            if (/Mac OS X/.test(ua)) {
                const match = ua.match(/Mac OS X ([\d_]+)/);
                return match ? `macOS ${match[1].replace(/_/g, '.')}` : "macOS";
            }
            
            if (/Linux/.test(ua)) return "Linux";
            if (/CrOS/.test(ua)) return "Chrome OS";
            
            return "Unknown OS";
        }

        function getConnectionType() {
            const connection = navigator.connection || navigator.mozConnection || navigator.webkitConnection;
            if (connection) {
                return connection.effectiveType || connection.type || 'Unknown';
            }
            return 'Unknown';
        }

        function loadDeviceInfo() {
            const nav = navigator;
            const screen = window.screen;
            const browserInfo = getDetailedBrowserInfo();

            deviceData = {
                browser: {
                    name: browserInfo.name,
                    version: browserInfo.version,
                    engine: browserInfo.engine,
                    cookiesEnabled: nav.cookieEnabled,
                    userAgent: nav.userAgent
                },
                system: {
                    os: getDetailedOS(),
                    platform: nav.platform || 'Unknown',
                    architecture: nav.userAgentData?.platform || 'Unknown',
                    cpuCores: nav.hardwareConcurrency || 'Unknown'
                },
                display: {
                    screenWidth: screen.width,
                    screenHeight: screen.height,
                    viewportWidth: window.innerWidth,
                    viewportHeight: window.innerHeight,
                    pixelRatio: window.devicePixelRatio,
                    colorDepth: screen.colorDepth
                },
                network: {
                    online: nav.onLine,
                    language: nav.language,
                    languages: nav.languages?.join(', ') || nav.language,
                    timezone: Intl.DateTimeFormat().resolvedOptions().timeZone,
                    connectionType: getConnectionType()
                },
                features: {
                    touchSupport: 'ontouchstart' in window || navigator.maxTouchPoints > 0,
                    webGL: !!window.WebGLRenderingContext,
                    localStorage: typeof Storage !== 'undefined',
                    serviceWorker: 'serviceWorker' in navigator,
                    notifications: 'Notification' in window
                }
            };

            updateUI();
        }

        function updateUI() {
            // Browser Information
            document.getElementById('browserName').textContent = deviceData.browser.name;
            document.getElementById('browserVersion').textContent = deviceData.browser.version;
            document.getElementById('browserEngine').textContent = deviceData.browser.engine;
            document.getElementById('cookiesEnabled').textContent = deviceData.browser.cookiesEnabled ? 'Enabled' : 'Disabled';

            // System Information
            document.getElementById('os').textContent = deviceData.system.os;
            document.getElementById('platform').textContent = deviceData.system.platform;
            document.getElementById('architecture').textContent = deviceData.system.architecture;
            document.getElementById('cpuCores').textContent = deviceData.system.cpuCores;

            // Display Information
            document.getElementById('screenResolution').textContent = 
                `${deviceData.display.screenWidth} × ${deviceData.display.screenHeight}`;
            document.getElementById('viewportSize').textContent = 
                `${deviceData.display.viewportWidth} × ${deviceData.display.viewportHeight}`;
            document.getElementById('pixelRatio').textContent = deviceData.display.pixelRatio;
            document.getElementById('colorDepth').textContent = `${deviceData.display.colorDepth} bits`;

            // Network & Location
            const onlineStatus = document.getElementById('onlineStatus');
            const statusDot = onlineStatus.querySelector('.status-dot');
            if (deviceData.network.online) {
                onlineStatus.innerHTML = '<span class="status-dot online"></span>Online';
            } else {
                onlineStatus.innerHTML = '<span class="status-dot offline"></span>Offline';
            }

            document.getElementById('language').textContent = deviceData.network.languages;
            document.getElementById('timezone').textContent = deviceData.network.timezone;
            document.getElementById('touchSupport').textContent = deviceData.features.touchSupport ? 'Yes' : 'No';

            // User Agent
            document.getElementById('userAgentString').textContent = deviceData.browser.userAgent;
        }

        function copyUserAgent() {
            navigator.clipboard.writeText(deviceData.browser.userAgent).then(() => {
                showToast('✅ User Agent copied to clipboard!');
            }).catch(err => {
                showToast('❌ Failed to copy User Agent');
                console.error('Copy failed:', err);
            });
        }

        function exportData() {
            const dataStr = JSON.stringify(deviceData, null, 2);
            const dataBlob = new Blob([dataStr], {type: 'application/json'});
            const url = URL.createObjectURL(dataBlob);
            
            const link = document.createElement('a');
            link.href = url;
            link.download = `device-info-${new Date().toISOString().slice(0,10)}.json`;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            URL.revokeObjectURL(url);
            
            showToast('📁 Device data exported successfully!');
        }

        function refreshData() {
            showToast('🔄 Refreshing device information...');
            setTimeout(() => {
                loadDeviceInfo();
                showToast('✅ Device information updated!');
            }, 500);
        }

        // Event listeners
        window.addEventListener('online', () => {
            deviceData.network.online = true;
            updateUI();
            showToast('🌐 Connection restored!');
        });

        window.addEventListener('offline', () => {
            deviceData.network.online = false;
            updateUI();
            showToast('📡 Connection lost!');
        });

        window.addEventListener('resize', () => {
            deviceData.display.viewportWidth = window.innerWidth;
            deviceData.display.viewportHeight = window.innerHeight;
            updateUI();
        });

        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            loadDeviceInfo();
            showToast('🚀 Device information loaded!');
        });
    </script>
</body>
</html>