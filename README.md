# BetSocial

Plataforma de apuestas casuales entre amigos con escrow automático en Stellar.

**Pitch core**: "Apuesta con tu grupo, el dinero queda guardado, y el ganador cobra automáticamente. Sin 'te pago después'."

## Problema

Las apuestas entre amigos tienen múltiples fricciones:
- "Te pago después" — No hay garantía de pago
- "Eso no cuenta" — No hay árbitro neutral
- Transferencias bancarias rompen la espontaneidad

Las casas de apuestas no resuelven esto — están diseñadas para apostar contra una empresa, no entre amigos.

## Solución

BetSocial usa Stellar para crear un **escrow automático**:
1. Dos amigos aceptan una apuesta
2. El dinero de ambos se bloquea instantáneamente
3. Cuando se resuelve, el ganador recibe todo automáticamente

Sin excusas. Sin depender de confianza.

## Features

- **Escrow automático** — Fondos bloqueados hasta resolución
- **Grupos privados** — Apuesta solo con tu círculo de confianza
- **Pools grupales** — No solo 1v1, todos participan
- **Retos personales** — "Bajo 3kg este mes o pierdo 10 lucas"
- **Perfil y estadísticas** — Rachas, % de victorias, historial
- **Medallas** — Logros absurdos como perder 5 veces seguidas
- **Árbitro social** — Si hay desacuerdo, un amigo del grupo decide

## Stack Técnico

- **Frontend**: Astro 5.17 + Tailwind CSS v4
- **Animaciones**: GSAP ScrollTrigger
- **Blockchain**: Stellar (Soroban para smart contracts)
- **Fuentes**: Space Grotesk + Inter

## ¿Por qué Stellar?

| Necesidad | Stellar lo resuelve |
|-----------|---------------------|
| Escrow automático | Smart contracts (Soroban) |
| Resolución instantánea | Finality en 5 seg |
| Apuestas de montos pequeños | Fees < $0.01 |
| Usuarios sin crypto | Wallets custodiales |

## Desarrollo

```bash
# Instalar dependencias
npm install

# Desarrollo
npm run dev

# Build
npm run build
```

## Contexto

Proyecto desarrollado para el **Build on Stellar Chile Ideatón** (DoraHacks).

- Deadline: 28 de febrero 2026
- Entregables: Video pitch 3 min + Mockup visual
