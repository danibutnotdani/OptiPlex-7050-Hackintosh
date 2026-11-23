# OptiPlex 7050 MT Hackintosh

EFI de OpenCore 1.0.4 para una Dell OptiPlex 7050 Mini Tower con macOS Sequoia 15.7.5. El equipo arranca también Windows y Linux, cada uno en su propio disco.

## Equipo

| Parte | Detalle |
| --- | --- |
| Modelo | Dell OptiPlex 7050 MT (Mini Tower) |
| Procesador | Intel Core i7-7700, 4 núcleos y 8 hilos (Kaby Lake) |
| Gráficos | Intel HD Graphics 630 |
| Memoria | 64 GB |
| Disco de macOS | Kingston NV3 de 500 GB (NVMe) |
| Otros discos | 2 × Kingston KC600 de 1 TB (SATA), para Windows y Linux |
| Audio | Realtek ALC255 (`alcid=11`) |
| Ethernet | Intel I219-LM (IntelMausi) |
| Wi-Fi | Adaptador USB TP-Link 802.11ac (RtWlanU) |
| Bluetooth | Adaptador USB Broadcom BCM4350C2 |
| Monitor | Dell P2424HT, 1920 × 1080 |
| SMBIOS | `Macmini8,1` |

## Qué incluye

- **ACPI:** `SSDT-EC`, `SSDT-HPET`, `SSDT-MCHC`, `SSDT-PLUG`.
- **Kexts activos:** Lilu, VirtualSMC, SMCProcessor, SMCSuperIO, SMCDellSensors, WhateverGreen, AppleALC, IntelMausi, RtWlanU, FeatureUnlock, RestrictEvents.
- **Kexts presentes pero desactivados:** AirportItlwm, IntelBluetoothFirmware, IntelBTPatcher, BlueToolFixup, HibernationFixup y un mapa USB hecho para la variante Micro (`OptiPlex7050_MFF_USBMap`), que no aplica a esta torre.
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
