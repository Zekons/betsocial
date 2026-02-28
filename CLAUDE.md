# BetSocial — Contexto del Proyecto

## Resumen
Plataforma de apuestas casuales entre amigos con escrow automático en Stellar. El dinero se bloquea al crear la apuesta y se libera automáticamente al ganador.

**Pitch core**: "Apuesta con tu grupo, el dinero queda guardado, y el ganador cobra automáticamente. Sin 'te pago después'."

---

## Estado Actual

### Landing Page ✅ COMPLETADA
- **Stack**: Astro 5.17 + Tailwind CSS v4 + GSAP (npm)
- **Paleta**:
  - Primary: Emerald `#10B981` (confianza, dinero)
  - Accent: Amber `#F59E0B` (emoción, CTAs)
  - Dark mode como base (`bg-base: #030712`)
- **Fuentes**: Space Grotesk (headings) + Inter (body)

---

## Componentes Completados

### Navbar (`src/components/landing/Navbar.astro`)
- Minimalista, dark mode
- Logo con icono + glow
- Links: Cómo funciona, Grupos, Seguridad
- CTA "Abrir App"
- Glass background con blur

### Hero (`src/components/landing/Hero.astro`)
- **Lado izquierdo**: Copy principal
  - Badge "X apuestas activas ahora" (contador live)
  - Headline: "Apuestas entre amigos. Sin complicaciones."
  - CTAs: "Invita a tu grupo" + "Ver cómo funciona"
  - Social proof: avatares apilados + "5,000+ grupos"

- **Lado derecho**: Phone mockup con chat animado
  - Simula conversación real ("Cabros de la U")
  - **Fase 1** (8s): Creación de apuesta
  - **Transición**: "Al día siguiente..."
  - **Fase 2**: Resolución con victoria
  - Chat posicionado abajo (justify-end) para parecer real

- **Elementos flotantes**: "+$5.000", "Tus grupos: 4", popup animado "+$2.000"

### HowItWorks (`src/components/landing/HowItWorks.astro`) ✅ COMPLETADO
**Sección con scroll horizontal disparado por scroll vertical (GSAP ScrollTrigger)**

- Container sticky de 450vh para 6 paneles
- Barra de progreso animada
- 6 pantallas de phone mockup mostrando el flujo completo:

#### Paso 1: Mis Grupos
- Lista de grupos con cards glass
- Avatares apilados por grupo
- Indicador de apuestas activas (🔥 + número)
- Monto en juego visible
- Botón "Crear apuesta"

#### Paso 2: Crear Apuesta (Modal)
- Bottom sheet sobre chat blurred
- Input "¿Qué apostamos?" (pre-llenado)
- Selector de monto ($500, $1.000, $2.000, Otro...)
- Selector "¿A quién?" con toggle Todos/Algunos
- Avatares seleccionables (Mati seleccionado)
- Botón "Enviar a Mati"

#### Paso 3: Aceptar Apuesta (Vista receptor)
- Chat view desde perspectiva de Mati
- Mensaje de propuesta en chat
- Card especial "Nueva Apuesta" con gradiente amber
- "@Mati propone:" con descripción
- Botones "Rechazar" / "Acepto"
- Chat posicionado abajo (justify-end)

#### Paso 4: Fondos Bloqueados (Modal)
- Modal centrado sobre chat blurred
- Icono candado verde
- "$2.000" total bloqueado
- Avatares Mati vs Tú con montos individuales
- Estado "Esperando resultado" con pulso
- Botón "Finalizar apuesta" (naranja oscuro)
- Logo Stellar (invertido a blanco) centrado abajo

#### Paso 5: Resolución / Victoria (Modal)
- Modal con borde verde
- Icono celebration
- "¡Ganaste!" + "+$2.000"
- Mati (perdedor, opaco, tachado) vs Tú (ganador, ring verde)
- Descripción de la apuesta
- Botones "Compartir" / "Cerrar"
- Logo Stellar en esquina superior derecha

#### Paso 6: Perfil ✅ COMPLETADO
- Header con avatar, username (@TuUsuario), fecha de registro
- Botón de configuración (settings)
- Stats grid: Total apuestas (23), % Ganadas (78%), Balance (+$45k)
- Card de racha con fuego animado (5 victorias, mejor: 8)
- Badges desbloqueados (🏆💎⚡🎯) + 1 bloqueado
- Historial reciente (últimas 3 apuestas con ganancia/pérdida)
- Bottom navigation (groups, chat, profile)

### Features (`src/components/landing/Features.astro`) ✅ COMPLETADO
**Bento grid con 6 características principales**

- Grid de 6 columnas para layouts asimétricos
- Animaciones reveal-left/reveal-right con stagger
- Cards:
  - **Escrow automático** (4 cols) — Fondos bloqueados hasta resolución
  - **Pago instantáneo** (2 cols) — Sin esperas
  - **Grupos privados** (3 cols) — Tu círculo de confianza
  - **Historial transparente** (3 cols) — Stats y rachas
  - **Sin intermediarios** (2 cols) — Sin comisiones ocultas
  - **Powered by Stellar** (4 cols) — <5s confirmación, <$0.01 fees

### FinalCTA (`src/components/landing/FinalCTA.astro`) ✅ COMPLETADO
- Card con gradiente primary → accent
- Círculos decorativos blur en esquinas
- Headline: "¿Listo para apostar con tus amigos?"
- Botón principal: "Invita a tu grupo"
- Link secundario: "Ver cómo funciona"

### Footer (`src/components/landing/Footer.astro`) ✅ COMPLETADO
- Logo + nombre BetSocial
- Links: Cómo funciona, Características, Términos, Privacidad
- Badge "Powered by Stellar"
- Copyright con mención al Ideatón

---

## Estructura de Archivos

```
betsocial/
├── CLAUDE.md                          ← Este archivo
├── public/
│   ├── stellar-logo.png               ← Logo original (175KB)
│   └── stellar-logo-small.png         ← Logo comprimido (2KB, 64x64)
├── src/
│   ├── layouts/Layout.astro           ← Google Fonts + scroll reveal
│   ├── styles/global.css              ← Paleta dark + animaciones
│   ├── pages/index.astro              ← Composición de landing
│   └── components/landing/
│       ├── Navbar.astro               ← Completado
│       ├── Hero.astro                 ← Completado
│       ├── HowItWorks.astro           ← Completado (scroll horizontal)
│       ├── Features.astro             ← Completado (bento grid)
│       ├── FinalCTA.astro             ← Completado
│       └── Footer.astro               ← Completado
└── astro.config.mjs
```

---

## Dependencias Clave

```json
{
  "gsap": "^3.x"  // Instalado via npm para ScrollTrigger
}
```

**Nota**: GSAP via CDN no funciona con Vite/Astro (error "Cannot set property window"). Usar siempre npm.

---

## Pendiente

### Landing Page ✅ COMPLETADA
1. ~~**HowItWorks**~~ ✅ Completado
2. ~~**Step 6 Perfil**~~ ✅ Completado
3. ~~**Features**~~ ✅ Completado (bento grid)
4. ~~**FinalCTA**~~ ✅ Completado
5. ~~**Footer**~~ ✅ Completado

### Video Pitch (3 min)
- [ ] Escribir guion
- [ ] Grabar video
- [ ] Subir a DoraHacks

---

## Notas Técnicas

### GSAP ScrollTrigger (HowItWorks)
```javascript
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

gsap.to(track, {
  x: -totalScroll,
  ease: 'none',
  scrollTrigger: {
    trigger: '.scroll-container',
    start: 'top top',
    end: 'bottom bottom',
    scrub: 1,
    invalidateOnRefresh: true
  }
});
```

### Logo Stellar invertido
```html
<img src="/stellar-logo-small.png" class="w-4 h-4 opacity-40 invert" />
```
- `invert` convierte negro a blanco via CSS filter

### Chat posicionado abajo
```html
<div class="flex-1 flex flex-col justify-end">
  <!-- mensajes aquí -->
</div>
```

---

## Decisiones de Diseño

### Scroll horizontal en HowItWorks:
- Más inmersivo que pasos estáticos
- Muestra el flujo real de la app
- El usuario "avanza" por la historia scrolleando
- 6 pantallas = suficiente contenido para justificar el sticky scroll

### Consistencia visual:
- Modales similares en pasos 4 y 5 (fondos bloqueados → victoria)
- Logo Stellar sutil en ambos modales
- Colores: verde para victoria, amber para acciones, primary para estados

### Terminología:
- Usamos "apuesta" no "reto" (más directo)
- "Enviar a [nombre]" en vez de "Retar a [nombre]"

---

## Comandos

```bash
# Desarrollo
cd betsocial && npm run dev   # Puerto 4321

# Build
npm run build

# Preview
npm run preview
```

---

## Contexto del Ideatón

- **Evento**: Build on Stellar Chile (DoraHacks)
- **Deadline**: 28 de febrero 2026
- **Entregables**: Video pitch 3 min + Mockup visual
- **NO se requiere código funcional**
- El código Astro es bonus para demo en video
