# Osmo Mobile 2 Remote

Controle remoto pelo navegador para o gimbal **DJI Osmo Mobile 2**, via **Web Bluetooth** (protocolo DUML da DJI). É uma página única (`index.html`), sem instalação nem servidor.

**Abrir:** https://guilhermecorrea77.github.io/osmo-mobile-remote/

## Recursos

- **Controle direcional** — D-pad com velocidade ajustável, centralizar, giros de 45°, *sweep* automático e bloqueio de pan/tilt.
- **Controle por mouse** — joystick virtual (zona morta, curva de precisão, parada suave) ou *mouse livre* (captura do ponteiro, estilo jogo).
- **Estabilização** — seguir a mão (Suave / Rápido / FPV em teste) ou posição fixa (Lock); desligar e religar os motores.
- **Visor LCD** com modo atual e ângulos reais enviados pelo gimbal; LED que pisca quando alguém aperta um botão no próprio gimbal.
- Atalhos de teclado e suporte a leitores de tela.

## Atalhos

| Tecla | Ação |
|---|---|
| `W` `A` `S` `D` / setas | mover |
| `Esc` / `C` | parar e centralizar |
| `P` / `T` | bloquear pan / tilt |
| `M` | seguir a mão ⇄ posição fixa |
| `L` | mouse livre |
| `+` / `−` | velocidade das setas |

## Requisitos

- **Chrome ou Edge** (Android, Windows, macOS, Linux). Safari/iOS e Firefox não têm Web Bluetooth.
- Página aberta por **HTTPS** (o GitHub Pages já serve assim) ou `localhost`.
- Gimbal ligado e **desconectado do app DJI Mimo** (só uma conexão BLE por vez).

## Como usar

1. Abra o link acima e toque em **Conectar Gimbal**.
2. Escolha o aparelho na lista (o campo *Filtro* aceita parte do nome, ex.: `Osmo`).
3. Use os controles. **Reconectar** volta ao mesmo aparelho sem escolher de novo.

## Notas técnicas

- Serviço BLE `FFF0`; escrita em `FFF5`, notificações em `FFF4`.
- Quadros DUML com CRC-8 no cabeçalho e CRC-16 no quadro; cmdset `0x04` (gimbal).
- Movimento contínuo por comandos relativos `04/14` a cada 100 ms, numa fila de escrita única (o GATT só aceita uma operação por vez).
- Ligar os motores de volta e o modo FPV ainda estão **em teste** no OM2.

> Projeto independente, sem vínculo com a DJI. Use por sua conta e risco.
