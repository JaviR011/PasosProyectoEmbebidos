# PasosProyectoEmbebidos


## Paso 1: Abrir bluetoothctl

Abre la terminal y ejecuta:

```bash
bluetoothctl
```

## Paso 2: Preparar bluetoothctl

En el prompt de `bluetoothctl`, escribe estos comandos uno por uno, pulsando Enter tras cada uno:

```bash
power on
agent on
default-agent
scan on
```

Esto activa el Bluetooth y comienza a buscar dispositivos.

## Paso 3: Emparejar y confiar en el dispositivo

Cuando veas en la lista tu dispositivo (por ejemplo, con MAC `00:21:13:01:14:9F` y nombre `Equipo10`), ejecuta:

```bash
pair 00:21:13:01:14:9F
trust 00:21:13:01:14:9F
connect 00:21:13:01:14:9F
```

Espera confirmaciones después de cada comando.

## Paso 4: Salir de bluetoothctl

```bash
exit
```

## Paso 5: Crear el puerto serial virtual (rfcomm)

Ejecuta en la terminal normal (fuera de bluetoothctl):

```bash
sudo rfcomm bind /dev/rfcomm0 00:21:13:01:14:9F 1
```

Esto crea el puerto `/dev/rfcomm0` para que puedas comunicarte con el módulo.


## Paso 6: Usar el puerto serial en tu aplicación

En tu programa Python o interfaz, abre `/dev/rfcomm0` para leer los datos Bluetooth.

---
