document.addEventListener('contextmenu', e => e.stopPropagation(), true);
document.oncontextmenu = null;
document.body.oncontextmenu = null;
document.body.style.userSelect = 'auto';
document.body.style.pointerEvents = 'auto';


=======================================================

// 🔓 Liberar copiar e colar (dentro <-> fora)

// --- Parte 1: liberar copiar de dentro pra fora ---
document.addEventListener('contextmenu', e => e.stopPropagation(), true);
document.oncontextmenu = null;
document.body.oncontextmenu = null;
document.body.style.userSelect = 'auto';
document.body.style.pointerEvents = 'auto';

// --- Parte 2: liberar colar de fora pra dentro ---
document.addEventListener('paste', e => e.stopPropagation(), true);

document.addEventListener('keydown', e => {
  if ((e.ctrlKey || e.metaKey) && e.key.toLowerCase() === 'v') {
    e.stopPropagation();
  }
}, true);

// limpar bloqueios de inputs e textareas
document.querySelectorAll('input, textarea, [contenteditable]').forEach(el => {
  el.onpaste = null;
  el.oncopy = null;
  el.oncut = null;
  el.onkeydown = null;
  el.onkeyup = null;
  el.onkeypress = null;
  el.style.userSelect = 'auto';
});
