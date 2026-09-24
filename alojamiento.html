/* ================================================================
   LÓGICA PRINCIPAL DEL SITIO
   Los textos están en js/translations.js y el contenido visual en modules/.
   ================================================================ */
const WEDDING_CONFIG = Object.freeze({
    password: '1234',
    weddingDate: '2027-06-19T18:00:00+02:00',
    defaultLang: 'es'
});

async function loadModules() {
    const modules = [
        ['view-home', 'modules/home.html'],
        ['view-ubicaciones', 'modules/ubicaciones.html'],
        ['view-alojamiento', 'modules/alojamiento.html']
    ];
    await Promise.all(modules.map(async ([id, url]) => {
        const target = document.getElementById(id);
        if (!target) return;
        const response = await fetch(url, { cache: 'no-cache' });
        if (!response.ok) throw new Error(`No se pudo cargar ${url}`);
        target.innerHTML = await response.text();
    }));
}

function goToPage(page) {
    ['home', 'ubicaciones', 'alojamiento'].forEach(p => {
        const view = document.getElementById('view-' + p);
        if (view) view.style.display = (p === page) ? '' : 'none';
    });
    document.querySelectorAll('.tabs button').forEach(btn => {
        btn.classList.toggle('active', btn.getAttribute('data-page') === page);
    });
}

function goToLocation(id) {
    goToPage('ubicaciones');
    requestAnimationFrame(() => {
        setTimeout(() => {
            const el = document.getElementById(id);
            if (!el) return;
            const header = document.getElementById('fixed-header');
            const headerOffset = (header && header.classList.contains('visible'))
                ? header.getBoundingClientRect().height : 0;
            const extraGap = 16;
            const targetTop = el.getBoundingClientRect().top + window.pageYOffset - headerOffset - extraGap;
            window.scrollTo({ top: targetTop, behavior: 'smooth' });
            el.classList.remove('highlight');
            void el.offsetWidth;
            el.classList.add('highlight');
            setTimeout(() => el.classList.remove('highlight'), 1700);
        }, 60);
    });
}

function toggleAcompanantes(show) {
    const box = document.getElementById('acomp-detail');
    const textarea = document.getElementById('f-acomp-nombres');
    if (!box || !textarea) return;
    if (show) {
        box.classList.add('open');
        textarea.setAttribute('required', 'required');
    } else {
        box.classList.remove('open');
        textarea.removeAttribute('required');
        textarea.value = '';
    }
}

function toggleFaq(btn) {
    const item = btn.parentElement;
    const answer = item.querySelector('.faq-answer');
    const isOpen = item.classList.contains('open');
    if (isOpen) {
        item.classList.remove('open');
        answer.style.maxHeight = null;
    } else {
        item.classList.add('open');
        answer.style.maxHeight = answer.scrollHeight + 'px';
    }
}

function setLang(lang) {
    const dict = window.TRANSLATIONS[lang];
    if (!dict) return;
    document.documentElement.lang = lang;
    document.title = dict.title;
    document.querySelectorAll('[data-i18n]').forEach(el => {
        const key = el.getAttribute('data-i18n');
        if (dict[key] !== undefined) el.innerHTML = dict[key];
    });
    document.getElementById('btn-cat').classList.toggle('active', lang === 'ca');
    document.getElementById('btn-esp').classList.toggle('active', lang === 'es');
    localStorage.setItem('wedding-lang', lang);
    document.querySelectorAll('.faq-item.open .faq-answer').forEach(answer => {
        answer.style.maxHeight = answer.scrollHeight + 'px';
    });
}

function initCountdown() {
    const weddingDate = new Date(WEDDING_CONFIG.weddingDate).getTime();
    function pad(n) { return String(n).padStart(2, '0'); }
    function updateCountdown() {
        const now = new Date().getTime();
        const diff = weddingDate - now;
        const els = {
            days: document.getElementById('cd-days'), hours: document.getElementById('cd-hours'),
            minutes: document.getElementById('cd-minutes'), seconds: document.getElementById('cd-seconds')
        };
        if (diff <= 0) { Object.values(els).forEach(el => el.textContent = '00'); return; }
        const days = Math.floor(diff / 86400000);
        const hours = Math.floor((diff % 86400000) / 3600000);
        const minutes = Math.floor((diff % 3600000) / 60000);
        const seconds = Math.floor((diff % 60000) / 1000);
        els.days.textContent = pad(days); els.hours.textContent = pad(hours);
        els.minutes.textContent = pad(minutes); els.seconds.textContent = pad(seconds);
    }
    updateCountdown();
    setInterval(updateCountdown, 1000);
}

function initRsvp() {
    const form = document.getElementById('rsvp-form');
    if (!form) return;
    form.addEventListener('submit', function(e) {
        e.preventDefault();
        const data = new FormData(form);
        fetch('/', {
            method: 'POST',
            headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
            body: new URLSearchParams(data).toString()
        })
        .then(() => {
            form.style.display = 'none';
            document.getElementById('rsvp-success').classList.add('visible');
        })
        .catch(() => alert('Hi ha hagut un problema enviant el formulari. Torna-ho a provar o escriu-nos directament.'));
    });
}

function initFixedHeader() {
    const tabs = document.querySelector('.hero .tabs');
    const langSwitch = document.querySelector('.lang-switch');
    const header = document.getElementById('fixed-header');
    if (!tabs || !langSwitch || !header) return;

    function pinTop() {
        return window.innerWidth <= 600 ? 40 : 22;
    }

    const placeholder = document.createElement('div');
    placeholder.setAttribute('aria-hidden', 'true');
    placeholder.style.visibility = 'hidden';
    placeholder.style.display = 'none';
    tabs.parentNode.insertBefore(placeholder, tabs);

    let pinned = false;
    function contentVisible() {
        const content = document.getElementById('site-content');
        return !!content && content.style.display !== 'none';
    }
    function pin() {
        const rect = tabs.getBoundingClientRect();
        placeholder.style.width = rect.width + 'px';
        placeholder.style.height = rect.height + 'px';
        placeholder.style.display = 'block';
        tabs.classList.add('pinned');
        langSwitch.classList.add('pinned');
        header.classList.add('visible');
        pinned = true;
    }
    function unpin() {
        tabs.classList.remove('pinned');
        langSwitch.classList.remove('pinned');
        header.classList.remove('visible');
        placeholder.style.display = 'none';
        pinned = false;
    }
    function onScroll() {
        if (!contentVisible()) {
            if (pinned) unpin();
            return;
        }
        if (!pinned) {
            if (tabs.getBoundingClientRect().top <= pinTop()) pin();
        } else if (placeholder.getBoundingClientRect().top > pinTop()) {
            unpin();
        }
    }
    window.addEventListener('scroll', onScroll, { passive: true });
    window.addEventListener('resize', onScroll, { passive: true });
    window.__syncFixedHeader = onScroll;
}

function initPasswordGate() {
    const gate = document.getElementById('password-gate');
    const content = document.getElementById('site-content');
    const form = document.getElementById('gate-form');
    const input = document.getElementById('gate-input');
    const error = document.getElementById('gate-error');
    function unlock() {
        gate.style.display = 'none'; content.style.display = '';
        try { sessionStorage.setItem('wedding-unlocked', '1'); } catch (e) {}
        if (window.__syncFixedHeader) requestAnimationFrame(window.__syncFixedHeader);
    }
    try { if (sessionStorage.getItem('wedding-unlocked') === '1') unlock(); } catch (e) {}
    const originalPlaceholder = input.placeholder;
    input.addEventListener('focus', () => input.placeholder = '');
    input.addEventListener('blur', () => { if (!input.value) input.placeholder = originalPlaceholder; });
    form.addEventListener('submit', e => {
        e.preventDefault(); const value = input.value.trim().toLowerCase();
        if (value === WEDDING_CONFIG.password.toLowerCase()) unlock();
        else { error.textContent = 'Contraseña incorrecta. Inténtalo de nuevo.'; input.value = ''; input.focus(); }
    });
}

(async function initSite() {
    initPasswordGate();
    try {
        await loadModules();
        initRsvp();
        initCountdown();
        initFixedHeader();
        const savedLang = localStorage.getItem('wedding-lang');
        setLang(savedLang === 'ca' ? 'ca' : WEDDING_CONFIG.defaultLang);
        goToPage('home');
        if (window.__syncFixedHeader) requestAnimationFrame(window.__syncFixedHeader);
    } catch (error) {
        console.error(error);
        document.getElementById('site-content').style.display = '';
        document.getElementById('site-content').insertAdjacentHTML('afterbegin', '<p style="padding:20px;text-align:center">No se ha podido cargar una parte de la página. Recarga la página.</p>');
    }
})();
