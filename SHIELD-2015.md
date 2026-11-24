# Clean Your TV para NVIDIA SHIELD TV 2015 (compilación no oficial)

**English below.**

## Qué es

**Clean Your TV** es una app **para el móvil Android** que limpia teles y reproductores Android TV
desde el propio móvil. Se conecta a la tele por la red de casa usando la *depuración en red* (ADB) de la
tele, analiza qué trae instalado y te propone:

- **Desactivar** apps preinstaladas, publicidad y telemetría que no usas. Se **desactivan**
  (`pm disable-user`), nunca se desinstalan, y todo se puede deshacer.
- Opcionalmente, poner una **pantalla de inicio limpia, sin anuncios**, en lugar de la de Google.
- Antes de tocar nada guarda un **punto de restauración**, y un vigilante devuelve la pantalla de
  inicio original si el cambio no se confirma en 150 segundos.

La app es de sus autores (proyecto [udhaykumarbala/cleanyourtv-app](https://github.com/udhaykumarbala/cleanyourtv-app),
licencia MIT) y las listas de cada tele salen de [Gathin23/cleanyourtv](https://github.com/Gathin23/cleanyourtv).

## Qué cambia en esta compilación

**Solo una cosa:** la app oficial no reconoce la **SHIELD TV 2015** (modelo P2571, `foster`).
Esta compilación la reconoce y le aplica la lista de la SHIELD TV 2017, que tiene el mismo chip
(Tegra X1) y el mismo firmware (SHIELD Experience 9.2.x, Android 11). Nada más está modificado.

- La lista propia de la SHIELD 2015 ya está aceptada en el proyecto original:
  [Gathin23/cleanyourtv#4431](https://github.com/Gathin23/cleanyourtv/pull/4431).
- El soporte en la app oficial está propuesto aquí:
  [udhaykumarbala/cleanyourtv-app#15774](https://github.com/udhaykumarbala/cleanyourtv-app/pull/15774).
  **Cuando salga una versión oficial con la SHIELD 2015, usa la oficial y desinstala esta.**

Probada en una SHIELD TV 2015 con Android 11 (RQ1A.210105.003): reconocida, limpieza aplicada,
pantalla de inicio nueva y varios reinicios sin problemas. Es **una sola unidad**.

## Riesgos y avisos (léelos)

- **No es oficial.** No la han revisado ni firmado los autores de la app. La compila GitHub Actions
  a partir del código de este fork, que puedes revisar.
- **Es una compilación de pruebas (debug).** Funciona igual, pero no está optimizada y va firmada con
  una clave temporal de GitHub. **Cada versión nueva tiene una firma distinta**: para actualizar hay
  que **desinstalar e instalar** otra vez. No se actualiza sola.
- **Mismo identificador que la app oficial.** Si tienes la oficial instalada, desinstálala antes.
  No pueden convivir.
- **La app da acceso a tu tele.** Para funcionar necesita la *depuración en red* de la tele, que abre
  el puerto 5555 **sin cifrar** a toda tu red. **Apágala cuando termines.**
- **Desactivar apps puede quitar funciones.** La lista se ha elegido con cuidado y protege lo
  necesario (mando, Chromecast, Asistente, actualizaciones, Plex/NAS de NVIDIA, etc.), pero cada
  casa es distinta. Revisa lo que te propone antes de aplicarlo.
- **Solo para SHIELD TV 2015.** En otras teles se comporta como la app oficial; para ellas usa la
  oficial.
- **Sin garantía** (licencia MIT): la usas bajo tu responsabilidad.

## Cómo deshacerlo

1. Desde la app: **restaurar** todo o una app concreta (usa el punto de restauración).
2. Con **«Guardar una copia»** al terminar, la app exporta scripts de restauración que funcionan con
   `adb` desde cualquier PC.
3. A mano: `adb shell pm enable <paquete>` para reactivar cualquier app.
4. Último recurso: restablecer de fábrica la SHIELD (pierdes apps y ajustes).

## Instalar

1. En el móvil, descarga el `.apk` de esta Release y ábrelo (permite instalar apps de origen
   desconocido si te lo pide).
2. Comprueba si quieres la suma SHA-256 que aparece en la Release.
3. En la SHIELD: *Ajustes → Preferencias del dispositivo → Información*, pulsa 7 veces
   *Compilación*; luego en *Opciones para desarrolladores* activa **Depuración de red**.
4. Abre la app en el móvil, elige tu SHIELD y sigue los pasos.

Compilado y publicado por **OUTSIDE** ([OUTSIDE2k8](https://github.com/OUTSIDE2k8)).

---

# Clean Your TV for the NVIDIA SHIELD TV 2015 (unofficial build)

## What it is

**Clean Your TV** is an **Android phone app** that cleans up Android TV sets and boxes from your phone.
It connects to the TV over your home network through the TV's *network debugging* (ADB), looks at what
is installed and offers to **disable** (never uninstall) preinstalled apps, ads and telemetry, and
optionally to set a **clean home screen without ads**. It saves a **restore point** first, and a
watchdog brings the stock home screen back if the change is not confirmed within 150 seconds.

The app belongs to its authors ([udhaykumarbala/cleanyourtv-app](https://github.com/udhaykumarbala/cleanyourtv-app),
MIT licence); the per TV lists come from [Gathin23/cleanyourtv](https://github.com/Gathin23/cleanyourtv).

## What this build changes

**One thing only:** the official app does not recognise the **SHIELD TV 2015** (P2571, `foster`).
This build does, and uses the SHIELD TV 2017 list for it (same Tegra X1, same SHIELD Experience 9.2.x,
Android 11). The 2015 list is merged upstream ([#4431](https://github.com/Gathin23/cleanyourtv/pull/4431))
and app support is proposed in [#15774](https://github.com/udhaykumarbala/cleanyourtv-app/pull/15774).
**Once an official release supports the SHIELD 2015, switch to it and uninstall this one.**
Tested on one SHIELD TV 2015, Android 11 (RQ1A.210105.003), including several reboots.

## Risks

- **Unofficial**, not reviewed or signed by the app's authors. Built by GitHub Actions from this fork's
  source.
- **Debug build**, signed with a throwaway key: **every build has a different signature**, so updating
  means uninstall and install again. No automatic updates.
- **Same application id as the official app**: uninstall the official one first; they cannot coexist.
- **Network debugging opens port 5555 unencrypted** to your whole network. **Switch it off afterwards.**
- **Disabling apps can remove features.** Review the plan before applying it.
- **For the SHIELD TV 2015 only.** For any other TV use the official app.
- **No warranty** (MIT licence). Use at your own risk.

## Undo

Restore from the app (restore point), the exported restore scripts ("Save a copy") with `adb` from any
PC, `adb shell pm enable <package>` by hand, or as a last resort a factory reset.

Built and published by **OUTSIDE** ([OUTSIDE2k8](https://github.com/OUTSIDE2k8)).
