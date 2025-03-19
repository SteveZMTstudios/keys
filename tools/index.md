# GnuPG/PGP Multi-platform Download

<style>
  .container {
    max-width: 900px;
    margin: 20px auto;
    padding: 0 15px;
  }
  .header {
    background: linear-gradient(120deg, #2196F3, #4CAF50);
    color: white;
    padding: 30px;
    border-radius: 8px;
    text-align: center;
    margin-bottom: 30px;
  }
  .countdown-box {
    text-align: center;
    margin: 30px 0;
    padding: 20px;
    border-radius: 8px;
    background-color: #f5f5f5;
  }
  .countdown {
    font-size: 3rem;
    font-weight: bold;
    color: #1976D2;
    animation: pulse 1s infinite;
  }
  @keyframes pulse {
    0% { opacity: 1; }
    50% { opacity: 0.7; }
    100% { opacity: 1; }
  }
  .os-card {
    transition: all 0.3s ease;
    cursor: pointer;
    margin-bottom: 20px;
    height: 100%;
    display: flex;
    flex-direction: column;
  }
  .os-card .mdui-card-primary {
    flex-shrink: 0;
  }
  .os-card .mdui-card-content {
    flex-grow: 1;
    height: 4.5em; /* 固定高度为3行文本 */
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }
  .os-card .mdui-card-actions {
    flex-shrink: 0;
  }
  .os-icon {
    font-size: 48px;
    margin: 20px 0;
  }
  .links-panel {
    margin-top: 40px;
  }
  .code-block {
    background: #272822;
    color: #f8f8f2;
    border-radius: 4px;
    padding: 15px;
    margin: 10px 0;
    overflow-x: auto;
    font-family: monospace;
  }
  .features-list {
    padding-left: 20px;
  }
  .features-list li {
    margin-bottom: 8px;
  }
</style>

<div class="container">
  <div class="header mdui-shadow-3">
    <h1>GnuPG/PGP Download List</h1>
    <p>We will automatically redirect you to the appropriate download page based on your device</p>
  </div>

  <div id="autoDetect" class="countdown-box mdui-shadow-2">
    <h2>Detected system: <span id="detectedOs" class="mdui-text-color-blue igTrans">Detecting...</span></h2>
    <div>Redirecting in <span class="countdown" id="countdown">5</span> seconds</div>
    <div class="mdui-btn-group mdui-m-t-3">
      <button id="cancelBtn" class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-pink">Cancel Redirect</button>
      <button id="jumpNowBtn" class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-blue">Redirect Now</button>
    </div>
  </div>

  <h2 class="mdui-text-center mdui-m-t-5">Select Your Platform</h2>
  
  <div class="mdui-row-md-4 mdui-row-sm-2 mdui-row-xs-1">
    <div class="mdui-col">
      <div class="mdui-card os-card" id="windowsCard">
        <div class="mdui-card-primary mdui-text-center igTrans">
          <div class="os-icon mdui-icon material-icons mdui-text-color-blue">&#xe30c;</div>
          <div class="mdui-card-primary-title">Windows</div>
        </div>
        <div class="mdui-card-content mdui-text-center">
          Gpg4win and portable versions for desktop user
        </div>
        <div class="mdui-card-actions mdui-text-center">
          <button class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-blue" onclick="expandOptions('windows')">View Options</button>
        </div>
      </div>
    </div>
    
    <div class="mdui-col">
      <div class="mdui-card os-card" id="linuxCard">
        <div class="mdui-card-primary mdui-text-center igTrans">
          <div class="os-icon mdui-icon material-icons mdui-text-color-green">&#xe86f;</div>
          <div class="mdui-card-primary-title">Linux</div>
        </div>
        <div class="mdui-card-content mdui-text-center">
          For various Linux distributions
        </div>
        <div class="mdui-card-actions mdui-text-center">
          <button class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-green" onclick="expandOptions('linux')">View Options</button>
        </div>
      </div>
    </div>
    
    <div class="mdui-col">
      <div class="mdui-card os-card" id="macCard">
        <div class="mdui-card-primary mdui-text-center igTrans">
          <div class="os-icon mdui-icon material-icons mdui-text-color-grey">&#xe320;</div>
          <div class="mdui-card-primary-title">macOS</div>
        </div>
        <div class="mdui-card-content mdui-text-center">
          Optimized for macOS users
        </div>
        <div class="mdui-card-actions mdui-text-center">
          <button class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-grey" onclick="expandOptions('mac')">View Options</button>
        </div>
      </div>
    </div>

    <div class="mdui-col">
      <div class="mdui-card os-card" id="androidCard">
        <div class="mdui-card-primary mdui-text-center igTrans">
          <div class="os-icon mdui-icon material-icons mdui-text-color-light-green">android</div>
          <div class="mdui-card-primary-title">Android</div>
        </div>
        <div class="mdui-card-content mdui-text-center">
          For Android phones and tablets
        </div>
        <div class="mdui-card-actions mdui-text-center">
          <button class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-light-green" onclick="expandOptions('android')">View Options</button>
        </div>
      </div>
    </div>
  </div>

  <!-- Windows Options Panel -->
  <div id="windowsOptions" class="mdui-panel mdui-panel-popout mdui-m-t-4" style="display:none;">
    <div class="mdui-panel-item mdui-panel-item-open">
      <div class="mdui-panel-item-header">
        <div class="mdui-panel-item-title">Windows Download Options</div>
       <!-- <i class="mdui-panel-item-arrow mdui-icon material-icons">&#xe313;</i>-->
      </div>
      <div class="mdui-panel-item-body">
        <div class="mdui-row-md-2 mdui-row-sm-1">
          <div class="mdui-col">
            <div class="mdui-card mdui-m-b-2">
              <div class="mdui-card-header">
                <div class="mdui-card-header-avatar mdui-icon material-icons">&#xe149;</div>
                <div class="mdui-card-header-title">Portable Version (Recommended)</div>
                <div class="mdui-card-header-subtitle">No installation required, works from USB drive</div>
              </div>
              <div class="mdui-card-content">
                <ul class="features-list">
                  <li>Lightweight version</li>
                  <li>No administrator rights required</li>
                  <li>Perfect for portable use</li>
                </ul>
              </div>
              <div class="mdui-card-actions">
                <a href="https://github.com/portapps/gnupg-portable/releases/download/2.4.3-12/gnupg-portable-win32-2.4.3-12-setup.exe" class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-blue-700" target="_blank">Download Portable Version</a>
              </div>
            </div>
          </div>
          <div class="mdui-col">
            <div class="mdui-card">
              <div class="mdui-card-header">
                <div class="mdui-card-header-avatar mdui-icon material-icons">&#xe30a;</div>
                <div class="mdui-card-header-title">Full Installation</div>
                <div class="mdui-card-header-subtitle">Standard Windows Installation</div>
              </div>
              <div class="mdui-card-content">
                <ul class="features-list">
                  <li>Provides complete functionality</li>
                  <li>Includes GUI interface</li>
                  <li>Higher system integration</li>
                </ul>
              </div>
              <div class="mdui-card-actions">
                <a href="https://gnupg.org/download/index.html#binary" class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-indigo" target="_blank">Download Full Version</a>
                <a href="https://gnupg.org/" class="mdui-btn mdui-ripple" target="_blank">Visit Official Website</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Linux Options Panel -->
  <div id="linuxOptions" class="mdui-panel mdui-panel-popout mdui-m-t-4" style="display:none;">
    <div class="mdui-panel-item mdui-panel-item-open">
      <div class="mdui-panel-item-header">
        <div class="mdui-panel-item-title">Linux Installation Options</div>
       <!-- <i class="mdui-panel-item-arrow mdui-icon material-icons">&#xe313;</i>-->
      </div>
      <div class="mdui-panel-item-body">
        <div class="mdui-row-md-2 mdui-row-sm-1">
          <div class="mdui-col">
            <div class="mdui-card mdui-m-b-2">
              <div class="mdui-card-header">
                <div class="mdui-card-header-avatar mdui-icon material-icons">&#xe5c3;</div>
                <div class="mdui-card-header-title">Kleopatra (Recommended)</div>
                <div class="mdui-card-header-subtitle">KDE Graphical Interface</div>
              </div>
              <div class="mdui-card-content">
                <p>Kleopatra is a graphical frontend for GnuPG, providing key management and file encryption features</p>
                <div class="code-block">
                  # Debian/Ubuntu<br>
                  sudo apt install kleopatra<br><br>
                  # Fedora<br>
                  sudo dnf install kleopatra
                </div>
              </div>
              <div class="mdui-card-actions">
                <a href="https://apps.kde.org/zh-cn/kleopatra/" class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-green-700" target="_blank">Visit Kleopatra</a>
                <a href="appstream://org.kde.kleopatra" class="mdui-btn mdui-ripple" target="_blank">AppStream Market</a>
                <a href="https://flathub.org/apps/org.kde.kleopatra" class="mdui-btn mdui-ripple igTrans" target="_blank">Flathub</a>
              </div>
            </div>
          </div>
          <div class="mdui-col">
            <div class="mdui-card">
              <div class="mdui-card-header">
                <div class="mdui-card-header-avatar mdui-icon material-icons">&#xe86f;</div>                
                <div class="mdui-card-header-title">Command Line Version</div>
                <div class="mdui-card-header-subtitle">For all Linux distributions</div>
              </div>
              <div class="mdui-card-content">
                <p>GnuPG core program:</p>
                <div class="code-block">
                  # Debian/Ubuntu<br>
                  sudo apt install gnupg<br><br>
                  # Fedora<br>
                  sudo dnf install gnupg<br><br>
                  # Arch Linux<br>
                  sudo pacman -S gnupg
                </div>
              </div>
              <div class="mdui-card-actions">
                <a href="https://gnupg.org/download/index.html" class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-green-900" target="_blank">Download Source Code</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Mac Options Panel -->
  <div id="macOptions" class="mdui-panel mdui-panel-popout mdui-m-t-4" style="display:none;">
    <div class="mdui-panel-item mdui-panel-item-open">
      <div class="mdui-panel-item-header">
        <div class="mdui-panel-item-title">macOS Installation Options</div>
       <!-- <i class="mdui-panel-item-arrow mdui-icon material-icons">&#xe313;</i>-->
      </div>
      <div class="mdui-panel-item-body">
        <div class="mdui-row-md-2 mdui-row-sm-1">
          <div class="mdui-col">
            <div class="mdui-card mdui-m-b-2">
              <div class="mdui-card-header">
                <div class="mdui-card-header-avatar mdui-icon material-icons">get_app</div>
                <div class="mdui-card-header-title">GPG Suite (Recommended)</div>
                <div class="mdui-card-header-subtitle">Designed specifically for macOS</div>
              </div>
              <div class="mdui-card-content">
                <p>GPG Suite provides a complete GnuPG toolkit for macOS, including a graphical interface</p>
              </div>
              <div class="mdui-card-actions">
                <a href="https://gpgtools.org/" class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-grey-700" target="_blank">Visit GPG Suite</a>
              </div>
            </div>
          </div>
          <div class="mdui-col">
            <div class="mdui-card">
              <div class="mdui-card-header">
                <div class="mdui-card-header-avatar mdui-icon material-icons">&#xe86f;</div>
                <div class="mdui-card-header-title">Install using Homebrew</div>
                <div class="mdui-card-header-subtitle">Command line method</div>
              </div>
              <div class="mdui-card-content">
                <div class="code-block">
                  # Install GnuPG<br>
                  brew install gnupg<br><br>
                  # Install Pinentry (password dialog)<br>
                  brew install pinentry-mac
                </div>
              </div>
              <div class="mdui-card-actions">
                <a href="https://formulae.brew.sh/formula/gnupg" class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-grey-800" target="_blank">Homebrew Page</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Android Options Panel -->
  <div id="androidOptions" class="mdui-panel mdui-panel-popout mdui-m-t-4" style="display:none;">
    <div class="mdui-panel-item mdui-panel-item-open">
      <div class="mdui-panel-item-header">
        <div class="mdui-panel-item-title">Android Installation Options</div>
       <!-- <i class="mdui-panel-item-arrow mdui-icon material-icons">&#xe313;</i>-->
      </div>
      <div class="mdui-panel-item-body">
        <div class="mdui-row-md-2 mdui-row-sm-1">
          <div class="mdui-col">
            <div class="mdui-card mdui-m-b-2">
              <div class="mdui-card-header">
                <div class="mdui-card-header-avatar mdui-icon material-icons">&#xe859;</div>
                <div class="mdui-card-header-title">OpenKeychain (Recommended)</div>
                <div class="mdui-card-header-subtitle">Open-source PGP implementation</div>
              </div>
              <div class="mdui-card-content">
                <p>OpenKeychain is the most popular OpenPGP implementation for Android, feature-rich and easy to use</p>
                <ul class="features-list">
                  <li>Manage PGP keys</li>
                  <li>Encrypt/decrypt files and messages</li>
                  <li>Support Smart card</li>
                  <li>Support for key servers</li>
                </ul>
              </div>
              <div class="mdui-card-actions">
                <a href="https://www.openkeychain.org/" class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-light-green-700" target="_blank">Official Website</a>
                <a href="https://play.google.com/store/apps/details?id=org.sufficientlysecure.keychain" class="mdui-btn mdui-ripple igTrans" target="_blank">Google Play</a>
                <a href="https://f-droid.org/packages/org.sufficientlysecure.keychain/" class="mdui-btn mdui-ripple igTrans" target="_blank">F-Droid</a>
              </div>
            </div>
          </div>
          <div class="mdui-col">
            <div class="mdui-card">
              <div class="mdui-card-header">
                <div class="mdui-card-header-avatar mdui-icon material-icons">&#xe051;</div>
                <div class="mdui-card-header-title">Encryption Online</div>
                <div class="mdui-card-header-subtitle">Use browser to encrypt data easily</div>
              </div>
              <div class="mdui-card-content">
                <p>Encrypt your data online using the browser, no installation required</p>
              </div>
              <div class="mdui-card-actions">
                <a href="./encrypt_sample.html" class="mdui-btn mdui-btn-raised mdui-ripple mdui-color-light-green-900" target="_blank">View Encryption Page</a>
                
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div id="allLinks" class="links-panel mdui-panel mdui-panel-popout mdui-m-t-4" style="display:none;">
    <div class="mdui-panel-item mdui-panel-item-open">
      <div class="mdui-panel-item-header">
        <div class="mdui-panel-item-title">All Download Links Summary</div>
       <!-- <i class="mdui-panel-item-arrow mdui-icon material-icons">&#xe313;</i>-->
      </div>
      <div class="mdui-panel-item-body">
        <div class="mdui-table-fluid">
          <table class="mdui-table mdui-table-hoverable">
            <thead>
              <tr>
                <th>Platform</th>
                <th>Name</th>
                <th>Link</th>
                <th>Description</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td class="igTrans"><i class="mdui-icon material-icons mdui-text-color-blue">&#xe30c;</i> Windows</td>
                <td>GnuPG Portable</td>
                <td><a href="https://github.com/portapps/gnupg-portable/releases/download/2.4.3-12/gnupg-portable-win32-2.4.3-12-setup.exe" target="_blank">Download</a></td>
                <td>No installation needed, portable</td>
              </tr>
              <tr>
                <td class="igTrans"><i class="mdui-icon material-icons mdui-text-color-blue">&#xe30c;</i> Windows</td>
                <td>Gpg4win Full Version</td>
                <td><a href="https://gnupg.org/download/index.html#binary" target="_blank">Download</a></td>
                <td>Complete installation package with GUI</td>
              </tr>
              <tr>
                <td class="igTrans"><i class="mdui-icon material-icons mdui-text-color-green">&#xe86f;</i> Linux</td>
                <td>Kleopatra</td>
                <td><a href="https://apps.kde.org/zh-cn/kleopatra/" target="_blank">Project Page</a></td>
                <td>KDE graphical key management tool</td>
              </tr>
              <tr>
                <td class="igTrans"><i class="mdui-icon material-icons mdui-text-color-grey">&#xe320;</i> macOS</td>
                <td>GPG Suite</td>
                <td><a href="https://gpgtools.org/" target="_blank">Download</a></td>
                <td>Complete toolkit for macOS</td>
              </tr>
              <tr>
                <td class="igTrans"><i class="mdui-icon material-icons mdui-text-color-light-green">&#xe859;</i> Android</td>
                <td>OpenKeychain</td>
                <td><a href="https://www.openkeychain.org/" target="_blank">Download</a></td>
                <td>Android platform encryption tool</td>
              </tr>
              <tr>
                <td class="igTrans"><i class="mdui-icon material-icons mdui-text-color-light-green">&#xe859;</i> Android</td>
                <td>Encryption Examples</td>
                <td><a href="./encrypt-sample" target="_blank">View</a></td>
                <td>Tutorials and examples</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- 添加主题切换按钮 -->
<button class="mdui-fab mdui-color-theme-accent mdui-ripple theme-switch" onclick="toggleTheme()">
  <i class="mdui-icon material-icons">&#xe3a9;</i>
</button>

<style>
  /* 主题切换按钮样式 */
  .theme-switch { 
    position: fixed; 
    bottom: 20px; 
    right: 20px; 
    z-index: 9999; 
  }
  
  * html .theme-switch { 
    position: absolute; 
    bottom: auto; 
    top: expression(eval(document.documentElement.scrollTop+document.documentElement.clientHeight-60)); 
  }
  
  /* 暗色模式下的样式调整 */
  .mdui-theme-layout-dark pre, .mdui-theme-layout-dark .code-block { 
    background: #1e1e1e; 
    color: #f0f0f0; 
  }
  
  .mdui-theme-layout-dark .countdown-box {
    background-color: #303030;
    color: #f0f0f0;
  }
  
  .mdui-theme-layout-dark .header {
    background: linear-gradient(120deg, #1565C0, #2E7D32);
  }
</style>

<script>
  // Device detection and redirection
  document.addEventListener('DOMContentLoaded', function() {
    const urlParams = new URLSearchParams(window.location.search);
    const autoParam = urlParams.get('auto');
    const autoJump = autoParam !== 'false';
    
    // Define default redirect links for each system
    const systemUrls = {
      windows: 'https://github.com/portapps/gnupg-portable/releases/download/2.4.3-12/gnupg-portable-win32-2.4.3-12-setup.exe',
      linux: 'https://apps.kde.org/zh-cn/kleopatra/',
      mac: 'https://gpgtools.org/',
      android: 'https://www.openkeychain.org/'
    };
    
    // Detect operating system/device type
    function detectDevice() {
      const ua = navigator.userAgent.toLowerCase();
      
      if (/android/i.test(ua)) return 'android';
      if (/iphone|ipad|ipod/i.test(ua)) return 'ios'; // Although no iOS option, we can detect it
      if (/mac os/i.test(ua)) return 'mac';
      if (/win/i.test(ua)) return 'windows';
      if (/linux/i.test(ua)) return 'linux';
      
      return 'other';
    }
    
    const detectedDevice = detectDevice();
    const deviceNames = {
      windows: 'Windows',
      linux: 'Linux',
      mac: 'macOS',
      android: 'Android',
      ios: 'iOS',
      other: 'Unknown Device'
    };
    
    // Update detected device
    document.getElementById('detectedOs').textContent = deviceNames[detectedDevice];

    // Add event listeners for card clicks
    document.getElementById('windowsCard').addEventListener('click', function() {
      expandOptions('windows');
    });
    
    document.getElementById('linuxCard').addEventListener('click', function() {
      expandOptions('linux');
    });
    
    document.getElementById('macCard').addEventListener('click', function() {
      expandOptions('mac');
    });
    
    document.getElementById('androidCard').addEventListener('click', function() {
      expandOptions('android');
    });
    
    // If URL parameter sets no auto-redirect
    if (!autoJump) {
      document.getElementById('autoDetect').style.display = 'none';
      document.getElementById('allLinks').style.display = 'block';
      return;
    }
    
    // Don't redirect for unsupported devices
    if (detectedDevice === 'ios' || detectedDevice === 'other') {
      document.getElementById('autoDetect').innerHTML = 
        '<div class="mdui-text-center mdui-typo-title mdui-text-color-orange">Your device (' + deviceNames[detectedDevice] + ') is not supported for automatic redirection</div>' +
        '<p class="mdui-text-center">Please select a suitable platform below</p>';
      return;
    }
    
    // Countdown and auto-redirect
    let count = 5;
    const countdownEl = document.getElementById('countdown');
    const countdownInterval = setInterval(() => {
      count--;
      countdownEl.textContent = count;
      
      if (count <= 0) {
        clearInterval(countdownInterval);
        window.location.href = systemUrls[detectedDevice];
      }
    }, 1000);
    
    // Cancel auto-redirect
    document.getElementById('cancelBtn').addEventListener('click', () => {
      clearInterval(countdownInterval);
      document.getElementById('autoDetect').innerHTML = 
        '<div class="mdui-text-center mdui-typo-title mdui-text-color-green">Auto-redirect cancelled</div>' +
        '<p class="mdui-text-center">Please select your required software version below</p>';
    });
    
    // Redirect now button
    document.getElementById('jumpNowBtn').addEventListener('click', () => {
      clearInterval(countdownInterval);
      window.location.href = systemUrls[detectedDevice];
    });
  });
  
  // Expand platform options
  function expandOptions(platform) {
    // Hide all option panels
    const allPanels = ['windowsOptions', 'linuxOptions', 'macOptions', 'androidOptions'];
    allPanels.forEach(id => {
      document.getElementById(id).style.display = 'none';
    });
    
    // Show the selected platform panel
    document.getElementById(platform + 'Options').style.display = 'block';
    
    // Smooth scroll to options area
    document.getElementById(platform + 'Options').scrollIntoView({ 
      behavior: 'smooth',
      block: 'start'
    });
    
    // Show selection effect
    const allCards = ['windowsCard', 'linuxCard', 'macCard', 'androidCard'];
    allCards.forEach(id => {
      document.getElementById(id).classList.remove('mdui-shadow-4');
    });
    document.getElementById(platform + 'Card').classList.add('mdui-shadow-4');
    
    // 已移除 snackbar 弹出通知
  }
  
  // 添加主题切换功能
  function toggleTheme() {
    var body = document.body;
    var hasClass = body.className.indexOf('mdui-theme-layout-dark') > -1;
    
    if (hasClass) {
      body.className = body.className.replace(/mdui-theme-layout-dark/g, '').trim();
    } else {
      body.className = body.className + ' mdui-theme-layout-dark';
    }
  }
  
  // 检测系统暗色模式偏好并应用
  document.addEventListener('DOMContentLoaded', function() {
    if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
      document.body.className += ' mdui-theme-layout-dark';
    }
    
    // 初始化主要UI组件
    if (typeof mdui !== 'undefined') {
      mdui.mutation();
    }
  });
  
  // 监听系统主题变化
  if (window.matchMedia) {
    try {
      var darkModeQuery = window.matchMedia('(prefers-color-scheme: dark)');
      var darkModeHandler = function(e) {
        if (e.matches) {
          document.body.className += ' mdui-theme-layout-dark';
        } else {
          document.body.className = document.body.className.replace(/mdui-theme-layout-dark/g, '').trim();
        }
      };
      
      if (darkModeQuery.addListener) {
        darkModeQuery.addListener(darkModeHandler);
      } else if (darkModeQuery.addEventListener) {
        darkModeQuery.addEventListener('change', darkModeHandler);
      }
    } catch(e) {
      console.error('media query error:', e);
    }
  }
</script>
