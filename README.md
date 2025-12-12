import React, { useRef, useEffect, useState } from 'react';

export default function AnimeTechBanner() {
  const canvasRef = useRef(null);
  const [downloading, setDownloading] = useState(false);

  useEffect(() => {
    const canvas = canvasRef.current;
    const ctx = canvas.getContext('2d');
    
    // Set canvas size
    canvas.width = 1600;
    canvas.height = 400;

    // Particle class
    class Particle {
      constructor() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.size = Math.random() * 3 + 1;
        this.speedX = Math.random() * 0.5 - 0.25;
        this.speedY = Math.random() * 0.5 - 0.25;
        this.opacity = Math.random() * 0.5 + 0.2;
      }
      
      update() {
        this.x += this.speedX;
        this.y += this.speedY;
        
        if (this.x > canvas.width) this.x = 0;
        if (this.x < 0) this.x = canvas.width;
        if (this.y > canvas.height) this.y = 0;
        if (this.y < 0) this.y = canvas.height;
      }
      
      draw() {
        ctx.fillStyle = `rgba(255, 100, 150, ${this.opacity})`;
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
        ctx.fill();
      }
    }

    // Create particles
    const particles = [];
    for (let i = 0; i < 50; i++) {
      particles.push(new Particle());
    }

    // Draw background gradient
    const drawBackground = () => {
      const gradient = ctx.createLinearGradient(0, 0, canvas.width, canvas.height);
      gradient.addColorStop(0, '#0a0a0a');
      gradient.addColorStop(0.5, '#1a1a1a');
      gradient.addColorStop(1, '#0f0f0f');
      ctx.fillStyle = gradient;
      ctx.fillRect(0, 0, canvas.width, canvas.height);
    };

    // Draw glowing circles
    const drawGlows = () => {
      // Red glow top right
      const redGlow = ctx.createRadialGradient(1200, 100, 0, 1200, 100, 200);
      redGlow.addColorStop(0, 'rgba(255, 50, 80, 0.2)');
      redGlow.addColorStop(1, 'transparent');
      ctx.fillStyle = redGlow;
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      // Blue glow bottom left
      const blueGlow = ctx.createRadialGradient(300, 350, 0, 300, 350, 150);
      blueGlow.addColorStop(0, 'rgba(0, 150, 255, 0.15)');
      blueGlow.addColorStop(1, 'transparent');
      ctx.fillStyle = blueGlow;
      ctx.fillRect(0, 0, canvas.width, canvas.height);
    };

    // Draw circuit lines
    const drawCircuits = () => {
      ctx.strokeStyle = 'rgba(0, 150, 255, 0.3)';
      ctx.lineWidth = 1;
      
      for (let i = 0; i < 5; i++) {
        ctx.beginPath();
        const y = 80 * i + 50;
        ctx.moveTo(0, y);
        ctx.lineTo(canvas.width, y);
        ctx.stroke();
      }
    };

    // Draw code fragments
    const drawCodeFragments = () => {
      ctx.font = '12px "Courier New"';
      ctx.fillStyle = 'rgba(0, 200, 255, 0.3)';
      const fragments = ['const', 'function', '{...}', 'async', '=>', 'import'];
      fragments.forEach((frag, i) => {
        ctx.fillText(frag, 200 + i * 250, 50 + i * 60);
      });
    };

    // Draw character circle
    const drawCharacter = () => {
      const x = 200;
      const y = 200;
      const radius = 140;

      // Glow
      const glow = ctx.createRadialGradient(x, y, radius - 20, x, y, radius + 30);
      glow.addColorStop(0, 'rgba(255, 50, 80, 0.3)');
      glow.addColorStop(1, 'transparent');
      ctx.fillStyle = glow;
      ctx.beginPath();
      ctx.arc(x, y, radius + 30, 0, Math.PI * 2);
      ctx.fill();

      // Circle border
      ctx.strokeStyle = 'rgba(255, 50, 80, 0.6)';
      ctx.lineWidth = 3;
      ctx.beginPath();
      ctx.arc(x, y, radius, 0, Math.PI * 2);
      ctx.stroke();

      // Inner gradient
      const innerGrad = ctx.createLinearGradient(x - radius, y - radius, x + radius, y + radius);
      innerGrad.addColorStop(0, '#1a1a1a');
      innerGrad.addColorStop(1, '#2a2a2a');
      ctx.fillStyle = innerGrad;
      ctx.beginPath();
      ctx.arc(x, y, radius, 0, Math.PI * 2);
      ctx.fill();

      // Placeholder text
      ctx.font = 'bold 80px Arial';
      ctx.fillStyle = 'rgba(255, 255, 255, 0.3)';
      ctx.textAlign = 'center';
      ctx.textBaseline = 'middle';
      ctx.fillText('👤', x, y);
    };

    // Draw text content
    const drawContent = () => {
      const startX = 420;
      
      // Name
      ctx.font = 'bold 52px "Segoe UI"';
      ctx.fillStyle = '#ffffff';
      ctx.shadowColor = 'rgba(255, 50, 80, 0.5)';
      ctx.shadowBlur = 20;
      ctx.textAlign = 'left';
      ctx.fillText('Sk Sumit Ahmed', startX, 100);
      ctx.shadowBlur = 0;

      // Username
      ctx.font = '24px "Segoe UI"';
      ctx.fillStyle = '#888888';
      ctx.fillText('sumitahmed', startX, 135);

      // Bio
      ctx.font = '18px "Segoe UI"';
      ctx.fillStyle = '#aaaaaa';
      ctx.fillText('💻  Full Stack Dev | Java, Python | DevOps & Cyber Security Enthusiast', startX, 180);
      ctx.fillText('🚀  Building innovative solutions • Open Source Contributor', startX, 210);

      // Tech badges
      const badges = [
        { text: 'React', color: 'rgba(255, 50, 80, 0.15)', border: 'rgba(255, 50, 80, 0.3)', textColor: '#ff6b9d' },
        { text: 'Node.js', color: 'rgba(255, 50, 80, 0.15)', border: 'rgba(255, 50, 80, 0.3)', textColor: '#ff6b9d' },
        { text: 'Python', color: 'rgba(0, 150, 255, 0.15)', border: 'rgba(0, 150, 255, 0.3)', textColor: '#4da6ff' },
        { text: 'Java', color: 'rgba(0, 150, 255, 0.15)', border: 'rgba(0, 150, 255, 0.3)', textColor: '#4da6ff' },
        { text: 'FastAPI', color: 'rgba(255, 50, 80, 0.15)', border: 'rgba(255, 50, 80, 0.3)', textColor: '#ff6b9d' },
        { text: 'Docker', color: 'rgba(0, 150, 255, 0.15)', border: 'rgba(0, 150, 255, 0.3)', textColor: '#4da6ff' },
        { text: 'MongoDB', color: 'rgba(255, 50, 80, 0.15)', border: 'rgba(255, 50, 80, 0.3)', textColor: '#ff6b9d' }
      ];

      let xOffset = startX;
      const yOffset = 250;
      badges.forEach(badge => {
        ctx.fillStyle = badge.color;
        ctx.strokeStyle = badge.border;
        ctx.lineWidth = 1;
        const width = ctx.measureText(badge.text).width + 28;
        
        ctx.beginPath();
        ctx.roundRect(xOffset, yOffset, width, 32, 6);
        ctx.fill();
        ctx.stroke();
        
        ctx.font = '13px "Segoe UI"';
        ctx.fillStyle = badge.textColor;
        ctx.fillText(badge.text, xOffset + 14, yOffset + 20);
        
        xOffset += width + 10;
      });

      // Stats
      ctx.font = '14px "Segoe UI"';
      ctx.fillStyle = '#666666';
      const stats = [
        { value: '28', label: 'Repos' },
        { value: '194', label: 'Stars' },
        { value: '802', label: 'Commits' }
      ];
      
      let statX = startX;
      stats.forEach(stat => {
        ctx.font = 'bold 20px "Segoe UI"';
        ctx.fillStyle = '#ffffff';
        ctx.fillText(stat.value, statX, 320);
        
        ctx.font = '14px "Segoe UI"';
        ctx.fillStyle = '#666666';
        const valueWidth = ctx.measureText(stat.value).width;
        ctx.fillText(stat.label, statX + valueWidth + 5, 320);
        
        statX += 120;
      });
    };

    // Animation loop
    const animate = () => {
      drawBackground();
      drawGlows();
      drawCircuits();
      drawCodeFragments();
      
      particles.forEach(particle => {
        particle.update();
        particle.draw();
      });
      
      drawCharacter();
      drawContent();
      
      requestAnimationFrame(animate);
    };

    animate();
  }, []);

  const downloadImage = () => {
    setDownloading(true);
    const canvas = canvasRef.current;
    const link = document.createElement('a');
    link.download = 'github-banner.png';
    link.href = canvas.toDataURL('image/png');
    link.click();
    setTimeout(() => setDownloading(false), 500);
  };

  return (
    <div className="flex flex-col items-center justify-center min-h-screen bg-zinc-900 p-8">
      <div className="mb-6">
        <h1 className="text-3xl font-bold text-white mb-2">GitHub Profile Banner Generator</h1>
        <p className="text-zinc-400 text-center">1600x400px • Optimized for GitHub README</p>
      </div>
      
      <canvas 
        ref={canvasRef}
        className="border-2 border-zinc-700 rounded-lg shadow-2xl mb-6"
        style={{ maxWidth: '100%', height: 'auto' }}
      />
      
      <div className="flex gap-4">
        <button
          onClick={downloadImage}
          disabled={downloading}
          className="px-6 py-3 bg-gradient-to-r from-pink-600 to-purple-600 text-white font-semibold rounded-lg hover:from-pink-700 hover:to-purple-700 transition-all shadow-lg hover:shadow-xl disabled:opacity-50"
        >
          {downloading ? 'Downloading...' : '⬇️ Download Banner (PNG)'}
        </button>
      </div>

      <div className="mt-8 max-w-2xl text-zinc-400 text-sm">
        <h3 className="text-white font-semibold mb-2">📝 How to use:</h3>
        <ol className="list-decimal list-inside space-y-1">
          <li>Click the download button to save your banner</li>
          <li>Upload the image to your GitHub repository (create a repo named after your username)</li>
          <li>In your README.md, add: <code className="bg-zinc-800 px-2 py-1 rounded">![Banner](./github-banner.png)</code></li>
          <li>Commit and your profile will show the new banner!</li>
        </ol>
      </div>
    </div>
  );
}
