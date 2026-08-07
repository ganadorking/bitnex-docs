# Copy Trading Automático

Copia automáticamente a los mejores traders de Hyperliquid desde Bitnex: el motor espeja sus operaciones en TU cuenta 24/7, proporcional a tu asignación, con tus propios límites de riesgo.

{% hint style="danger" %}
**Advertencia de riesgo.** El copy trading ejecuta órdenes REALES en tu cuenta y puede generar pérdidas, incluida la pérdida **parcial o total** del capital asignado. Rendimientos pasados no garantizan resultados futuros. Bitnex NO es gestor de capital ni asesor financiero: la decisión de copiar a un trader es exclusivamente tuya.
{% endhint %}

## Cómo funciona (en 5 pasos)

1. **Elige un trader** — en el Top 100, la Clasificación, o pega cualquier wallet de Hyperliquid (Snipers). Cada perfil muestra estadísticas reales: PnL, ROI, drawdown máximo, Sharpe, win rate, posiciones e historial.
2. **Configura tu copia** — asignación en USDC, modo Copytrade o Contraria, apalancamiento máximo, desviación máxima de entrada, protección de pérdida, y opcionalmente qué activos copiar o si sembrar las posiciones que el trader ya tiene abiertas.
3. **Firma los términos** (una sola vez por wallet) y **aprueba la agent key** de copias — una llave que **solo puede operar, NUNCA retirar**, y que puedes revocar on-chain cuando quieras. Si ya tienes una de una copia anterior, "Usar existente" no pide ninguna firma.
4. **El motor copia 24/7** — espeja los cambios NUEVOS de posición del trader (aperturas, aumentos, reducciones, cierres **y sus TP/SL**), proporcional a tu asignación. Cada orden copiada queda marcada con el chip "Copy" en tus tablas.
5. **Pausa, ajusta o detén cuando quieras.** Detener una copia **no cierra tus posiciones abiertas** — se quedan en tu cuenta y las gestionas tú desde el Portafolio.

## ¿Necesito dejar la wallet conectada?

**No.** La copia corre en los servidores de Bitnex con la agent key: no necesitas tener la wallet conectada, la página abierta ni el equipo encendido. La agent key se guarda **cifrada** (AES-256-GCM) y solo el motor puede usarla — y únicamente para operar, jamás para retirar fondos.

## El tamaño de tus copias

Las copias son **proporcionales**: si el trader arriesga el 10% de su equity en una operación, tu copia arriesga el 10% de tu asignación. Ejemplo: trader con $500,000 de equity abre una posición de $50,000 (10%) → con una asignación de $100, tu copia abre ~$10.

* **Mínimo por orden:** Hyperliquid exige ~$10 de nocional por orden. Si tu asignación es muy pequeña frente al equity del trader, algunas copias no alcanzarán el mínimo y se saltarán (lo verás en "Última actividad").
* **Saldo mínimo:** necesitas al menos **$20 USDC** en tu cuenta de perps para activar una copia, y tu asignación no puede superar tu saldo.
* **Sin margen suficiente:** si tu cuenta se queda sin margen, las copias simplemente **no se ejecutan** hasta que vuelvas a tener saldo. Nada se rompe: el motor sigue vigilando y retoma cuando hay margen.

## Los controles de riesgo

| Control | Qué hace |
| --- | --- |
| **Apalancamiento máximo** (1–40×) | Tus copias espejan el leverage del trader hasta este tope, y tu posición copiada nunca supera asignación × leverage. |
| **Desviación máxima de entrada** (1–20% o sin límite) | Si al ejecutarse tu copia el precio ya se movió en tu contra más de este % respecto a la entrada del trader, esa copia se salta. *No aplica a la siembra de posiciones ya abiertas.* |
| **Protección de pérdida** (−10 / −25 / −50%) | Si la copia (solo lo abierto por el motor) pierde ese % de tu asignación entre realizado y no realizado, se cierran las posiciones copiadas y la copia se pausa automáticamente. |
| **Activos** | Copia todos los mercados del trader o solo los que selecciones. |
| **Copiar posiciones ya abiertas** | Al iniciar, abre proporcionalmente las posiciones actuales del trader **a precio actual**. |

## Modo Contraria (inverso)

En modo Contraria, cuando el trader abre long tú abres **short** (y viceversa). Los cierres siempre actúan sobre TU posición real, y sus TP/SL se invierten con lógica: el TP del trader pasa a ser tu SL y viceversa (misma barrera de precio, posición opuesta). Aplican los mismos límites de riesgo.

## Qué se copia y qué no

* ✅ Aperturas, aumentos, reducciones y cierres de **perps** del dex principal.
* ✅ **TP/SL del trader** (espejados y actualizados si los mueve).
* ✅ Cierre total del trader ⇒ cierre total de tu copia.
* ❌ Spot, staking y mercados HIP-3 (por ahora).
* ❌ El portafolio HISTÓRICO del trader — solo cambios desde que activas la copia (salvo que actives "copiar posiciones ya abiertas").

## Retrasos y diferencias de precio

El motor revisa a los traders en ciclos de ~5 segundos. Entre la operación del trader y tu copia pueden existir **retrasos y diferencias de precio** (servidores, red, ejecución de Hyperliquid): tus resultados pueden diferir de los del trader, incluso significativamente. La desviación máxima de entrada existe precisamente para acotar este efecto.

## Comisiones

Las órdenes copiadas pagan la comisión estándar de Bitnex (builder fee) de la superficie de copy trading — por defecto, la misma tasa que el terminal Pro. No hay comisión de gestión ni de rendimiento: no cobramos un % de tus ganancias.

## Pausar, detener y revocar

* **Pausar**: el motor deja de abrir Y de cerrar. Todo pasa a depender de ti al 100%: si el trader cierra, tu cuenta NO cierra. Tus posiciones y TP/SL quedan como están.
* **Detener y eliminar**: borra la copia y su agent key cifrada del servidor. Tus posiciones abiertas permanecen — gestiónalas desde el Portafolio.
* **Revocar on-chain**: puedes invalidar la agent key en cualquier momento desde Hyperliquid (la clave con nombre "bitnex-copy").

## Términos y condiciones (texto firmado)

Al activar el copy trading firmas con tu wallet el siguiente texto canónico (versión `v1-2026-08`). Tu wallet te muestra el texto íntegro en el momento de firmar, y la firma queda registrada como constancia criptográfica de tu aceptación.

> **Bitnex Copy Trading — Aceptación de riesgos (v1-2026-08)**
>
> Al firmar, declaro y acepto que:
>
> 1. El copy trading ejecuta órdenes REALES en mi cuenta de forma automática, y puedo perder PARCIAL o TOTALMENTE el capital asignado, igual que el trader copiado.
> 2. Bitnex NO es gestor de capital, NO es asesor financiero y NADA en la plataforma constituye una recomendación o propósito de inversión. La decisión de copiar a un trader es EXCLUSIVAMENTE mía; para asesoría real debo acudir a profesionales financieros especializados.
> 3. Pueden existir RETRASOS o diferencias de precio entre la operación del trader y mi copia (servidores, red, ejecución de Hyperliquid); mis resultados pueden diferir de los del trader, incluso significativamente.
> 4. Bitnex y cualquier persona relacionada NO se hacen responsables de pérdidas, ajustes, cambios de configuración, interrupciones del servicio, errores de ejecución o cualquier otro daño derivado del uso del copy trading.
> 5. Rendimientos pasados del trader copiado NO garantizan resultados futuros.
> 6. Detener una copia NO cierra mis posiciones abiertas: gestionarlas es mi responsabilidad.
> 7. La agent key que autorizo solo puede operar (nunca retirar) y puedo revocarla on-chain cuando quiera.

## Preguntas frecuentes

**¿Qué pasa si cierro el navegador o desconecto la wallet?**
Nada: la copia sigue corriendo en el servidor con la agent key. Conectar la wallet solo hace falta para crear, ajustar, pausar o detener copias.

**¿Si el trader cierra su posición, la mía se cierra sola?**
Sí, mientras la copia esté ACTIVA. En pausa, no — todo depende de ti.

**¿Puedo copiar a varios traders a la vez?**
Sí, cada copia es independiente con su propia asignación y límites.

**¿Puedo operar mi cuenta manualmente mientras copio?**
Sí. El motor solo toca lo que él abrió (lleva su propio registro de lotes); tus posiciones personales no disparan la protección ni se cierran por la copia. Ojo: comparten el mismo margen de la cuenta.

**¿Por qué una operación del trader no se copió?**
Mira "Última actividad" en tu copia: las razones típicas son desviación de entrada superada, nocional por debajo del mínimo (~$10), tope de asignación × leverage alcanzado, o falta de margen.

**¿La puntuación /100 qué mide?**
Es una heurística transparente sobre datos reales: rentabilidad 30d (35%), consistencia/Sharpe (20%), riesgo por drawdown (20%), win rate (15%) y actividad (10%). No es una recomendación de inversión.
