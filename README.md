<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1180 610" width="1180" height="610">
  <defs>
    <!-- Background Gradients -->
    <radialGradient id="bgGlow1" cx="20%" cy="30%" r="50%">
      <stop offset="0%" stop-color="#7C3AED" stop-opacity="0.15" />
      <stop offset="100%" stop-color="#030712" stop-opacity="0" />
    </radialGradient>
    <radialGradient id="bgGlow2" cx="80%" cy="80%" r="50%">
      <stop offset="0%" stop-color="#22D3EE" stop-opacity="0.15" />
      <stop offset="100%" stop-color="#030712" stop-opacity="0" />
    </radialGradient>
    <radialGradient id="bgGlow3" cx="50%" cy="50%" r="50%">
      <stop offset="0%" stop-color="#10B981" stop-opacity="0.1" />
      <stop offset="100%" stop-color="#030712" stop-opacity="0" />
    </radialGradient>

    <!-- Accent Linear Gradients -->
    <linearGradient id="accentGrad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" stop-color="#7C3AED" />
      <stop offset="50%" stop-color="#22D3EE" />
      <stop offset="100%" stop-color="#10B981" />
    </linearGradient>
    
    <linearGradient id="asciiGrad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" stop-color="#22D3EE">
        <animate attributeName="stop-color" values="#22D3EE;#7C3AED;#22D3EE" dur="8s" repeatCount="indefinite" />
      </stop>
      <stop offset="100%" stop-color="#7C3AED">
        <animate attributeName="stop-color" values="#7C3AED;#10B981;#7C3AED" dur="8s" repeatCount="indefinite" />
      </stop>
    </linearGradient>

    <!-- UI Borders -->
    <linearGradient id="glassBorder" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" stop-color="rgba(255,255,255,0.15)" />
      <stop offset="100%" stop-color="rgba(255,255,255,0.02)" />
    </linearGradient>

    <!-- Filters -->
    <filter id="blurHeavy" x="-20%" y="-20%" width="140%" height="140%">
      <feGaussianBlur stdDeviation="40" />
    </filter>
    <filter id="glow">
      <feGaussianBlur stdDeviation="3" result="coloredBlur"/>
      <feMerge>
        <feMergeNode in="coloredBlur"/>
        <feMergeNode in="SourceGraphic"/>
      </feMerge>
    </filter>
    
    <filter id="noiseFilter">
      <feTurbulence type="fractalNoise" baseFrequency="0.75" numOctaves="3" stitchTiles="stitch"/>
      <feColorMatrix type="matrix" values="1 0 0 0 0, 0 1 0 0 0, 0 0 1 0 0, 0 0 0 0.04 0" />
    </filter>

    <!-- Clip Paths -->
    <clipPath id="terminalClip">
      <rect width="660" height="510" x="460" y="50" rx="16" />
    </clipPath>
  </defs>

  <style>
    /* Typography & Core */
    * { box-sizing: border-box; }
    .font-sans { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; }
    .font-mono { font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, Courier, monospace; }
    
    /* Animations */
    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
    }
    
    @keyframes scanline {
      0% { transform: translateY(-50px); opacity: 0; }
      10% { opacity: 0.5; }
      90% { opacity: 0.5; }
      100% { transform: translateY(600px); opacity: 0; }
    }

    @keyframes blink {
      0%, 100% { opacity: 1; }
      50% { opacity: 0; }
    }

    @keyframes pulseGlow {
      0%, 100% { opacity: 0.8; filter: drop-shadow(0 0 8px rgba(34, 211, 238, 0.4)); }
      50% { opacity: 1; filter: drop-shadow(0 0 15px rgba(34, 211, 238, 0.8)); }
    }

    @keyframes revealLine {
      from { opacity: 0; transform: translateX(-10px); }
      to { opacity: 1; transform: translateX(0); }
    }

    /* Typewriter Text Setup */
    .typing-wrapper { position: relative; display: inline-block; }
    .type-text { 
      opacity: 0; 
      animation: roleCycle 12s infinite; 
      fill: url(#accentGrad);
      font-weight: 700;
    }
    .type-text-1 { animation-delay: 0s; }
    .type-text-2 { animation-delay: 4s; }
    .type-text-3 { animation-delay: 8s; }

    @keyframes roleCycle {
      0%, 5% { opacity: 0; clip-path: inset(0 100% 0 0); }
      10%, 25% { opacity: 1; clip-path: inset(0 0 0 0); }
      30%, 100% { opacity: 0; clip-path: inset(0 0 0 0); }
    }

    .cursor {
      fill: #22D3EE;
      animation: blink 1s step-end infinite;
    }

    /* Staggered Reveals */
    .reveal-1 { animation: revealLine 0.6s ease-out 0.5s both; }
    .reveal-2 { animation: revealLine 0.6s ease-out 0.8s both; }
    .reveal-3 { animation: revealLine 0.6s ease-out 1.1s both; }
    .reveal-4 { animation: revealLine 0.6s ease-out 1.4s both; }
    .reveal-5 { animation: revealLine 0.6s ease-out 1.7s both; }
    .reveal-skills { animation: revealLine 0.8s ease-out 2s both; }

    /* ASCII Animation */
    .ascii-line { opacity: 0; animation: revealLine 0.1s ease-out forwards; }
    /* Injecting delays via nth-child logic conceptually or inline */
    
    /* Interactive Pills (Hover simulated via SVG standard pseudo-classes) */
    .skill-pill { cursor: pointer; transition: all 0.3s ease; }
    .skill-pill:hover rect {
      stroke: #22D3EE;
      fill: rgba(34, 211, 238, 0.1);
      filter: drop-shadow(0 0 8px rgba(34,211,238,0.4));
    }
    .skill-pill:hover text { fill: #fff; }
    
    .social-icon { cursor: pointer; transition: all 0.3s ease; fill: #94A3B8; }
    .social-icon:hover {
      fill: #22D3EE;
      filter: drop-shadow(0 0 8px rgba(34,211,238,0.6));
      transform: translateY(-2px);
    }
  </style>

  <!-- 1. Background Layer -->
  <rect width="100%" height="100%" fill="#030712" />
  
  <!-- Animated Glow Orbs -->
  <g filter="url(#blurHeavy)">
    <circle cx="20%" cy="20%" r="250" fill="url(#bgGlow1)">
      <animateTransform attributeName="transform" type="translate" values="0,0; 30,20; 0,0" dur="15s" repeatCount="indefinite"/>
    </circle>
    <circle cx="80%" cy="70%" r="300" fill="url(#bgGlow2)">
      <animateTransform attributeName="transform" type="translate" values="0,0; -40,-20; 0,0" dur="20s" repeatCount="indefinite"/>
    </circle>
    <circle cx="50%" cy="50%" r="200" fill="url(#bgGlow3)">
      <animateTransform attributeName="transform" type="translate" values="0,0; 20,-30; 0,0" dur="18s" repeatCount="indefinite"/>
    </circle>
  </g>

  <!-- Noise Overlay -->
  <rect width="100%" height="100%" style="pointer-events:none;" filter="url(#noiseFilter)" />

  <!-- 2. Main Glass Panel -->
  <rect x="10" y="10" width="1160" height="590" rx="20" fill="#0F172A" fill-opacity="0.6" stroke="url(#glassBorder)" stroke-width="1.5" />
  
  <!-- Outer border shimmer -->
  <rect x="10" y="10" width="1160" height="590" rx="20" fill="none" stroke="url(#accentGrad)" stroke-width="1" opacity="0.3" filter="url(#glow)">
    <animate attributeName="opacity" values="0.1;0.4;0.1" dur="4s" repeatCount="indefinite"/>
  </rect>

  <!-- ======================== LEFT SIDE: ASCII ART ======================== -->
  <g transform="translate(40, 60)" style="animation: float 6s ease-in-out infinite;">
    <text class="font-mono" fill="url(#asciiGrad)" font-size="11.5" font-weight="bold" letter-spacing="1" style="white-space: pre;" filter="url(#glow)">
      <tspan x="0" y="15" class="ascii-line" style="animation-delay: 0.1s;">      ::.                              .::      </tspan>
      <tspan x="0" y="30" class="ascii-line" style="animation-delay: 0.15s;">     .::::.                          .::::.     </tspan>
      <tspan x="0" y="45" class="ascii-line" style="animation-delay: 0.2s;">    .:::::::.                      .:::::::.    </tspan>
      <tspan x="0" y="60" class="ascii-line" style="animation-delay: 0.25s;">   :::::::::::..                ..:::::::::::   </tspan>
      <tspan x="0" y="75" class="ascii-line" style="animation-delay: 0.3s;">  ;;;;;;;;;;;;;;;;.          .;;;;;;;;;;;;;;;;  </tspan>
      <tspan x="0" y="90" class="ascii-line" style="animation-delay: 0.35s;">  ;;;;;;;;;;;;;;;;;;;;    ;;;;;;;;;;;;;;;;;;;;  </tspan>
      <tspan x="0" y="105" class="ascii-line" style="animation-delay: 0.4s;">  ;;;;;;;;;;;;;;;;;;;;;  ;;;;;;;;;;;;;;;;;;;;;  </tspan>
      <tspan x="0" y="120" class="ascii-line" style="animation-delay: 0.45s;">  $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$  </tspan>
      <tspan x="0" y="135" class="ascii-line" style="animation-delay: 0.5s;">  $$$$$$$$$$$ \/ \/ \/ \/ \/ \/ $$$$$$$$$$$$$$  </tspan>
      <tspan x="0" y="150" class="ascii-line" style="animation-delay: 0.55s;">  $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$  </tspan>
      <tspan x="0" y="165" class="ascii-line" style="animation-delay: 0.6s;">  $$$$$$$$$$$  [SYSTEM SECURED]  $$$$$$$$$$$$$  </tspan>
      <tspan x="0" y="180" class="ascii-line" style="animation-delay: 0.65s;">  %%%%%%%%%%%  _ _ _ _ _ _ _ _   %%%%%%%%%%%%%  </tspan>
      <tspan x="0" y="195" class="ascii-line" style="animation-delay: 0.7s;">  %%%%%%%%%%% / | | | | | | | \  %%%%%%%%%%%%%  </tspan>
      <tspan x="0" y="210" class="ascii-line" style="animation-delay: 0.75s;">  %%%%%%%%%%% | | | | | | | | |  %%%%%%%%%%%%%  </tspan>
      <tspan x="0" y="225" class="ascii-line" style="animation-delay: 0.8s;">   %%%%%%%%%% \_|_|_|_|_|_|_|_/  %%%%%%%%%%    </tspan>
      <tspan x="0" y="240" class="ascii-line" style="animation-delay: 0.85s;">    %%%%%%%%%%                  %%%%%%%%%%     </tspan>
      <tspan x="0" y="255" class="ascii-line" style="animation-delay: 0.9s;">     %%%%%%%%%%                %%%%%%%%%%      </tspan>
      <tspan x="0" y="270" class="ascii-line" style="animation-delay: 0.95s;">       %%%%%%%%%%            %%%%%%%%%%        </tspan>
      <tspan x="0" y="285" class="ascii-line" style="animation-delay: 1.0s;">         ##########        ##########          </tspan>
      <tspan x="0" y="300" class="ascii-line" style="animation-delay: 1.05s;">           ##########    ##########            </tspan>
      <tspan x="0" y="315" class="ascii-line" style="animation-delay: 1.1s;">             ####################              </tspan>
      <tspan x="0" y="330" class="ascii-line" style="animation-delay: 1.15s;">               ################                </tspan>
      <tspan x="0" y="345" class="ascii-line" style="animation-delay: 1.2s;">                  ##########                   </tspan>
      <tspan x="0" y="360" class="ascii-line" style="animation-delay: 1.25s;">                     ####                      </tspan>
    </text>
    <rect x="0" y="380" width="10" height="15" class="cursor" />
  </g>

  <!-- Scanline over left section -->
  <rect x="20" y="0" width="400" height="10" fill="url(#accentGrad)" opacity="0.3" style="animation: scanline 4s linear infinite; pointer-events: none;" filter="url(#glow)"/>

  <!-- Vertical Divider -->
  <line x1="430" y1="50" x2="430" y2="560" stroke="rgba(255,255,255,0.08)" stroke-width="1" />

  <!-- ======================== RIGHT SIDE: TERMINAL ======================== -->
  <g transform="translate(460, 50)">
    <!-- Terminal Background -->
    <rect width="680" height="510" rx="16" fill="#000000" fill-opacity="0.3" stroke="rgba(255,255,255,0.06)" stroke-width="1" />
    
    <!-- Mac Window Controls -->
    <circle cx="24" cy="24" r="6" fill="#EF4444" opacity="0.8" />
    <circle cx="44" cy="24" r="6" fill="#F59E0B" opacity="0.8" />
    <circle cx="64" cy="24" r="6" fill="#10B981" opacity="0.8" />
    <text x="90" y="28" fill="#94A3B8" class="font-mono" font-size="12">~/developer/profile — bash</text>
    <line x1="0" y1="48" x2="680" y2="48" stroke="rgba(255,255,255,0.05)" stroke-width="1" />

    <!-- Terminal Content Area -->
    <g transform="translate(30, 90)">
      
      <!-- Greeting -->
      <text x="0" y="0" fill="#F8FAFC" class="font-sans" font-size="38" font-weight="800" letter-spacing="-0.5">
        Hi 👋 I'm Diego Fernando
      </text>

      <!-- Animated Typed Roles -->
      <g transform="translate(0, 45)">
        <text x="0" y="0" class="font-sans type-text type-text-1" font-size="24">> Computer Science Student @ UIS</text>
        <text x="0" y="0" class="font-sans type-text type-text-2" font-size="24">> Full Stack Web Developer</text>
        <text x="0" y="0" class="font-sans type-text type-text-3" font-size="24">> Biomedical Tech Enthusiast</text>
        <!-- Static cursor blinking at fixed position roughly matching longest line -->
        <rect x="420" y="-20" width="12" height="26" class="cursor" />
      </g>

      <!-- Info List (Sequential Reveal) -->
      <g class="font-mono" font-size="14" fill="#94A3B8" transform="translate(0, 100)">
        <g class="reveal-1" transform="translate(0, 0)">
          <text x="0" y="0" fill="#7C3AED" font-weight="bold">const</text>
          <text x="45" y="0" fill="#F8FAFC">location</text>
          <text x="120" y="0" fill="#22D3EE">=</text>
          <text x="140" y="0" fill="#10B981">'Bucaramanga, Colombia'</text>
          <text x="330" y="0">;</text>
        </g>

        <g class="reveal-2" transform="translate(0, 35)">
          <text x="0" y="0" fill="#7C3AED" font-weight="bold">const</text>
          <text x="45" y="0" fill="#F8FAFC">education</text>
          <text x="125" y="0" fill="#22D3EE">=</text>
          <text x="145" y="0" fill="#10B981">'Universidad Industrial de Santander'</text>
          <text x="440" y="0">;</text>
        </g>

        <g class="reveal-3" transform="translate(0, 70)">
          <text x="0" y="0" fill="#7C3AED" font-weight="bold">const</text>
          <text x="45" y="0" fill="#F8FAFC">focus</text>
          <text x="95" y="0" fill="#22D3EE">=</text>
          <text x="115" y="0" fill="#10B981">['LMS Platforms', '3D Maps', 'Algorithms']</text>
          <text x="435" y="0">;</text>
        </g>

        <g class="reveal-4" transform="translate(0, 105)">
          <text x="0" y="0" fill="#7C3AED" font-weight="bold">const</text>
          <text x="45" y="0" fill="#F8FAFC">portfolio</text>
          <text x="125" y="0" fill="#22D3EE">=</text>
          <text x="145" y="0" fill="#10B981">'github.com/DiegoChamarravi'</text>
          <text x="360" y="0">;</text>
        </g>

        <g class="reveal-5" transform="translate(0, 140)">
          <text x="0" y="0" fill="#7C3AED" font-weight="bold">let</text>
          <text x="35" y="0" fill="#F8FAFC">status</text>
          <text x="95" y="0" fill="#22D3EE">=</text>
          <text x="115" y="0" fill="#10B981">'Building the future... 🚀'</text>
          <text x="320" y="0">;</text>
        </g>
      </g>

      <!-- Skills / Technologies Section -->
      <g class="reveal-skills" transform="translate(0, 280)">
        <text x="0" y="0" fill="#F8FAFC" class="font-sans" font-size="16" font-weight="600" letter-spacing="1">TECH_STACK.json</text>
        
        <g transform="translate(0, 20)" class="font-sans" font-size="13" font-weight="500" fill="#94A3B8">
          
          <!-- Row 1 -->
          <g class="skill-pill" transform="translate(0, 0)">
            <rect width="80" height="32" rx="16" fill="rgba(15,23,42,0.6)" stroke="rgba(255,255,255,0.1)" />
            <text x="40" y="21" text-anchor="middle">React</text>
          </g>
          <g class="skill-pill" transform="translate(90, 0)">
            <rect width="90" height="32" rx="16" fill="rgba(15,23,42,0.6)" stroke="rgba(255,255,255,0.1)" />
            <text x="45" y="21" text-anchor="middle">Node.js</text>
          </g>
          <g class="skill-pill" transform="translate(190, 0)">
            <rect width="105" height="32" rx="16" fill="rgba(15,23,42,0.6)" stroke="rgba(255,255,255,0.1)" />
            <text x="52.5" y="21" text-anchor="middle">TypeScript</text>
          </g>
          <g class="skill-pill" transform="translate(305, 0)">
            <rect width="85" height="32" rx="16" fill="rgba(15,23,42,0.6)" stroke="rgba(255,255,255,0.1)" />
            <text x="42.5" y="21" text-anchor="middle">Express</text>
          </g>
          <g class="skill-pill" transform="translate(400, 0)">
            <rect width="70" height="32" rx="16" fill="rgba(15,23,42,0.6)" stroke="rgba(255,255,255,0.1)" />
            <text x="35" y="21" text-anchor="middle">MySQL</text>
          </g>
          <g class="skill-pill" transform="translate(480, 0)">
            <rect width="80" height="32" rx="16" fill="rgba(15,23,42,0.6)" stroke="rgba(255,255,255,0.1)" />
            <text x="40" y="21" text-anchor="middle">LaTeX</text>
          </g>

          <!-- Row 2 -->
          <g class="skill-pill" transform="translate(0, 42)">
            <rect width="95" height="32" rx="16" fill="rgba(15,23,42,0.6)" stroke="rgba(255,255,255,0.1)" />
            <text x="47.5" y="21" text-anchor="middle">JavaScript</text>
          </g>
          <g class="skill-pill" transform="translate(105, 42)">
            <rect width="90" height="32" rx="16" fill="rgba(15,23,42,0.6)" stroke="rgba(255,255,255,0.1)" />
            <text x="45" y="21" text-anchor="middle">Next.js</text>
          </g>
          <g class="skill-pill" transform="translate(205, 42)">
            <rect width="95" height="32" rx="16" fill="rgba(15,23,42,0.6)" stroke="rgba(255,255,255,0.1)" />
            <text x="47.5" y="21" text-anchor="middle">Tailwind</text>
          </g>
          <g class="skill-pill" transform="translate(310, 42)">
            <rect width="80" height="32" rx="16" fill="rgba(15,23,42,0.6)" stroke="rgba(255,255,255,0.1)" />
            <text x="40" y="21" text-anchor="middle">Python</text>
          </g>
          <g class="skill-pill" transform="translate(400, 42)">
            <rect width="80" height="32" rx="16" fill="rgba(15,23,42,0.6)" stroke="rgba(255,255,255,0.1)" />
            <text x="40" y="21" text-anchor="middle">Docker</text>
          </g>
        </g>
      </g>
      
      <!-- Social Icons Panel -->
      <g transform="translate(0, 395)" class="reveal-skills">
        <line x1="0" y1="0" x2="620" y2="0" stroke="rgba(255,255,255,0.05)" stroke-width="1" />
        
        <!-- GitHub -->
        <g transform="translate(10, 20)" class="social-icon">
          <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
        </g>
        
        <!-- LinkedIn -->
        <g transform="translate(60, 20)" class="social-icon">
          <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
        </g>
        
        <!-- Twitter -->
        <g transform="translate(110, 21)" class="social-icon">
          <path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/>
        </g>

        <!-- Portfolio Globe -->
        <g transform="translate(160, 20)" class="social-icon">
          <path d="M12 0c-6.627 0-12 5.373-12 12s5.373 12 12 12 12-5.373 12-12-5.373-12-12-12zm1 22.928c-4.606-.475-8.31-3.923-9.155-8.428h5.275c.427 3.58 1.758 6.666 3.88 8.428zm0-10.428h-5.918c-.053-.488-.082-.99-.082-1.5s.029-1.012.082-1.5h5.918v3zm0-5h-5.275c.845-4.505 4.549-7.953 9.155-8.428-2.122 1.762-3.453 4.848-3.88 8.428zm2 15.428c2.122-1.762 3.453-4.848 3.88-8.428h5.275c-.845 4.505-4.549 7.953-9.155 8.428zm4-10.428c.053-.488.082-.99.082-1.5s-.029-1.012-.082-1.5h5.918c-.845 4.505-4.549 7.953-9.155 8.428zm-4-13.428c4.606.475 8.31 3.923 9.155 8.428h-5.275c-.427-3.58-1.758-6.666-3.88-8.428z"/>
        </g>
      </g>
    </g>
  </g>
</svg>
