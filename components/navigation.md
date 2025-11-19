# Cyberpunk Navigation Styling

## CSS for Navigation Components

```css
/* Cyberpunk Navigation Styles */
.cyberpunk-navigation {
  margin-top: 2rem;
  border-top: 2px solid #00FFFF;
  background: linear-gradient(135deg, rgba(0, 17, 17, 0.9) 0%, rgba(13, 23, 23, 0.9) 100%);
}

.slide-header {
  padding: 1rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: rgba(0, 255, 255, 0.1);
  border-bottom: 1px solid #00FFFF;
}

.terminal-prompt {
  color: #00FFFF;
  font-weight: bold;
  text-shadow: 0 0 10px #00FFFF;
  font-family: 'Monaco', 'Consolas', 'Courier New', monospace;
  font-size: 1rem;
}

.slide-counter {
  color: #00FF41;
  font-weight: bold;
  font-family: 'Monaco', 'Consolas', 'Courier New', monospace;
  text-shadow: 0 0 8px #00FF41;
}

.slide-navigation {
  padding: 1.5rem 2rem;
}

.nav-controls {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.nav-btn {
  background: #0D1117;
  border: 2px solid #00FFFF;
  color: #00FFFF;
  padding: 0.8rem 1.5rem;
  font-family: 'Monaco', 'Consolas', 'Courier New', monospace;
  font-weight: bold;
  text-transform: uppercase;
  cursor: pointer;
  transition: all 0.3s ease;
  border-radius: 4px;
  font-size: 0.9rem;
  min-width: 120px;
}

.nav-btn:hover:not(:disabled) {
  background: #00FFFF;
  color: #000011;
  box-shadow: 0 0 20px #00FFFF, 0 0 30px #00FFFF;
  transform: scale(1.05);
}

.nav-btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  border-color: #666;
  color: #666;
}

.nav-btn:disabled:hover {
  background: #0D1117;
  color: #666;
  transform: none;
  box-shadow: none;
}

.btn-glow {
  display: inline-block;
  transition: all 0.3s ease;
}

.progress-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.ascii-progress {
  font-family: 'Monaco', 'Consolas', 'Courier New', monospace;
  font-size: 0.9rem;
  color: #00FF41;
  text-shadow: 0 0 8px #00FF41;
}

.progress-bar {
  color: #00FF41;
  text-shadow: 0 0 8px #00FF41;
}

.progress-percent {
  color: #FFB000;
  font-weight: bold;
  text-shadow: 0 0 8px #FFB000;
}

/* Responsive Design */
@media (max-width: 768px) {
  .nav-controls {
    flex-direction: column;
    gap: 1rem;
  }

  .nav-btn {
    padding: 0.6rem 1.2rem;
    font-size: 0.8rem;
    min-width: 100px;
  }

  .slide-header {
    padding: 0.8rem 1rem;
    flex-direction: column;
    gap: 0.5rem;
    text-align: center;
  }

  .terminal-prompt, .slide-counter {
    font-size: 0.9rem;
  }
}

@media (max-width: 480px) {
  .progress-container {
    order: -1;
    margin-bottom: 1rem;
  }

  .nav-controls {
    flex-direction: row;
    justify-content: space-between;
  }

  .ascii-progress {
    font-size: 0.7rem;
  }
}

/* Animation Effects */
@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.7;
  }
}

.nav-btn.active {
  animation: pulse 2s infinite;
}

/* Keyboard Navigation Hints */
.nav-btn::after {
  content: '';
  position: absolute;
  bottom: -20px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 0.7rem;
  color: #666;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.nav-btn:hover::after {
  opacity: 1;
}

.prev-btn::after {
  content: '← Left Arrow';
}

.next-btn::after {
  content: 'Right Arrow →';
}
```

## JavaScript for Keyboard Navigation

```javascript
// Keyboard navigation support
document.addEventListener('DOMContentLoaded', function() {
  // Get current slide number from URL or slide counter
  function getCurrentSlide() {
    const path = window.location.pathname;
    const match = path.match(/(\d+)-/);
    return match ? parseInt(match[1]) : 0;
  }

  // Keyboard event handler
  document.addEventListener('keydown', function(e) {
    const currentSlide = getCurrentSlide();

    switch(e.key) {
      case 'ArrowRight':
      case ' ':
      case 'Enter':
        e.preventDefault();
        const nextBtn = document.querySelector('.next-btn');
        if (nextBtn && !nextBtn.disabled) {
          nextBtn.click();
        }
        break;

      case 'ArrowLeft':
      case 'Backspace':
        e.preventDefault();
        const prevBtn = document.querySelector('.prev-btn');
        if (prevBtn && !prevBtn.disabled) {
          prevBtn.click();
        }
        break;

      case 'Home':
        e.preventDefault();
        window.location.href = 'index';
        break;

      case 'End':
        e.preventDefault();
        window.location.href = '16-resources-questions';
        break;

      case 'Escape':
        e.preventDefault();
        window.location.href = 'index';
        break;
    }
  });

  // Add visual feedback for active navigation
  const navButtons = document.querySelectorAll('.nav-btn');
  navButtons.forEach(btn => {
    btn.addEventListener('mouseenter', function() {
      this.classList.add('active');
    });

    btn.addEventListener('mouseleave', function() {
      this.classList.remove('active');
    });
  });

  // Update progress bar animation
  const progressBar = document.querySelector('.progress-bar');
  if (progressBar) {
    progressBar.style.animation = 'pulse 3s infinite ease-in-out';
  }
});

// Touch/swipe support for mobile
let touchStartX = null;
let touchStartY = null;

document.addEventListener('touchstart', function(e) {
  touchStartX = e.touches[0].clientX;
  touchStartY = e.touches[0].clientY;
});

document.addEventListener('touchend', function(e) {
  if (!touchStartX || !touchStartY) return;

  const touchEndX = e.changedTouches[0].clientX;
  const touchEndY = e.changedTouches[0].clientY;

  const diffX = touchStartX - touchEndX;
  const diffY = touchStartY - touchEndY;

  // Only trigger if horizontal swipe is dominant
  if (Math.abs(diffX) > Math.abs(diffY) && Math.abs(diffX) > 50) {
    if (diffX > 0) {
      // Swipe left - next slide
      const nextBtn = document.querySelector('.next-btn');
      if (nextBtn && !nextBtn.disabled) {
        nextBtn.click();
      }
    } else {
      // Swipe right - previous slide
      const prevBtn = document.querySelector('.prev-btn');
      if (prevBtn && !prevBtn.disabled) {
        prevBtn.click();
      }
    }
  }

  touchStartX = null;
  touchStartY = null;
});
```

## Usage Instructions

### For MonkeysPaw Integration:

1. **Include in each slide**: Add the navigation HTML structure at the bottom of each slide
2. **CSS Integration**: The styles should be included in the main stylesheet or loaded per page
3. **JavaScript Loading**: Include the JavaScript in a script tag or external file
4. **Responsive Design**: Navigation adapts to mobile and tablet screens
5. **Accessibility**: Full keyboard and touch navigation support

### Navigation Features:

- **Keyboard Shortcuts**: Arrow keys, Space, Enter, Home, End, Escape
- **Touch Gestures**: Swipe left/right for next/previous
- **Visual Feedback**: Hover effects, progress indication, disabled states
- **Responsive**: Mobile-first design with touch-friendly buttons
- **Accessibility**: Clear focus indicators and semantic navigation

### Progress Bar Logic:

Each slide shows completion percentage based on slide number:
- Slide 1: 6% (1/16)
- Slide 8: 50% (8/16)
- Slide 16: 100% (16/16)

The ASCII progress bar fills proportionally with █ characters.