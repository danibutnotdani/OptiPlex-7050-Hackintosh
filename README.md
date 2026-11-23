# OptiPlex 7050 Hackintosh

EFI de OpenCore para una Dell OptiPlex 7050 Micro con macOS Sequoia 15.7.5.

## Equipo

| Parte | Detalle |
| --- | --- |
| Procesador | Intel Core i7-7700 (Kaby Lake) |
| Gráficos | Intel HD Graphics 630 |
| Memoria | 64 GB |
| Audio | Realtek ALC255 (`alcid=11`) |
| Ethernet | Intel (IntelMausi) |
| Wi-Fi | Adaptador USB Realtek (RtWlanU) |
| SMBIOS | `Macmini8,1` |

## Qué incluye

- **ACPI:** `SSDT-EC`, `SSDT-HPET`, `SSDT-MCHC`, `SSDT-PLUG`.
- **Kexts activos:** Lilu, VirtualSMC, SMCProcessor, SMCSuperIO, SMCDellSensors, WhateverGreen, AppleALC, IntelMausi, RtWlanU, FeatureUnlock, RestrictEvents.
- **Kexts presentes pero desactivados:** AirportItlwm, IntelBluetoothFirmware, IntelBTPatcher, BlueToolFixup, HibernationFixup y un mapa USB.
- **Argumentos de arranque:** `alcid=11 revpatch=sbvmm igfxrpsc=1`.
- **Gráficos:** parche de framebuffer para las salidas de video (conectores 0 a 2).

## Antes de usarla

El `config.plist` viene **sin números de serie**. En `PlatformInfo > Generic` debes poner los tuyos:

1. Genera un juego para `Macmini8,1` con [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS).
2. Llena `SystemSerialNumber`, `MLB` y `SystemUUID`.
3. Pon en `ROM` la dirección MAC de tu tarjeta de red.

Sin esto iMessage y FaceTime no funcionan.

## Advertencia

Es la configuración de un equipo concreto. Si tu hardware o tu versión de BIOS difieren, úsala como referencia y sigue la [guía de Dortania](https://dortania.github.io/OpenCore-Install-Guide/). Haz respaldo de tu EFI actual antes de reemplazarla.
