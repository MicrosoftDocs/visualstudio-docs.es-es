---
title: Requisitos de sistema del emulador de Visual Studio para Android | Microsoft Docs
ms.custom: ''
ms.prod: visual-studio-dev15
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f1462769a4ba9929a000bca998c1fe3708908798
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272045"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Requisitos de sistema del Emulador de Visual Studio para Android

El emulador de Visual Studio para Android se ejecuta como una máquina virtual en Hyper-V, que es la tecnología de virtualización para Windows 8 y posteriores. Para ejecutar el emulador, el equipo debe cumplir los requisitos para ejecutar Hyper-V, tal como se describe en este tema.

El programa de instalación intenta configurar estos requisitos previos de forma automática cuando se instala el emulador. Si el programa de instalación logra configurar correctamente los requisitos previos, el emulador funciona según lo previsto. En caso contrario, habrá que habilitar manualmente los requisitos previos. Si tiene que configurar manualmente los requisitos previos, los pasos y herramientas son los mismos que los descritos [aquí](/previous-versions/windows/apps/jj863509\(v=vs.105\)) para el emulador de Windows Phone.

> [!IMPORTANT]
> El programa de instalación del emulador comprueba si se cumplen los requisitos previos para la ejecución del emulador de Visual Studio para Android. Si esos requisitos no se cumplen, se muestran una serie de advertencias, pero no se exigirá su cumplimiento.

## <a name="Checklist"></a> Lista de comprobación rápida

Esta lista de comprobación rápida muestra los requisitos para la ejecución del emulador de Visual Studio para Android. Para obtener información más detallada, vea las secciones posteriores de este tema.

Requisitos del sistema

- Compatibilidad con Hyper-V (vea más abajo los requisitos de Hyper-V)

- 6 GB o más de RAM

- Versión de 64 bits de la edición Pro de Windows 8, Windows 8.1, Windows10 o superior

- Un procesador que admita SSSE3 o posterior.

Requisitos de red

- DHCP

- Configuración de puerta de enlace y DNS configurada automáticamente

Requisitos de Hyper-V

- En el BIOS, deben admitirse las siguientes características:

  - Virtualización asistida por hardware

  - Traducción de direcciones de segundo nivel (SLAT)

  - Prevención de ejecución de datos (DEP) basada en hardware

- En Windows, Hyper-V debe estar habilitado y en ejecución.

- Debe ser miembro del grupo local Administradores de Hyper-V.

## <a name="system-requirements"></a>Requisitos del sistema
 Su equipo debe cumplir los siguientes requisitos:

- Compatibilidad con Hyper-V (vea [Requisitos de Hyper-V](#hyper-v-requirements))

- 6 GB o más de RAM

- Versión de 64 bits de la edición Pro de Windows 8, Windows 8.1, Windows10 o superior.

Para comprobar los requisitos de RAM y de Windows, vaya al Panel de control, elija Sistema y seguridad y, a continuación, elija Sistema.

![Comprobación de los requisitos del sistema](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")

## <a name="network-requirements"></a>Requisitos de red

La red debe cumplir los siguientes requisitos:

- DHCP

   El emulador requiere DHCP porque se configura automáticamente como un dispositivo independiente en la red, con su propia dirección IP.

- Configuración de puerta de enlace y DNS configurada automáticamente

   No es posible definir manualmente la configuración DNS y de puerta de enlace.

  Para solucionar problemas de red en el emulador, vea los temas siguientes:

- [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requirements"></a>Requisitos de Hyper-V

Requisitos de Hyper-V en el BIOS

El BIOS del equipo debe admitir y tener habilitadas las siguientes características:

- Virtualización asistida por hardware

- Traducción de direcciones de segundo nivel (SLAT)

- Prevención de ejecución de datos (DEP) basada en hardware

Requisitos de Hyper-V en Windows

Una vez que el equipo y el BIOS están configurados para admitir Hyper-V, el programa de instalación habilita e inicia Hyper-V. En caso contrario, habrá que habilitar manualmente los requisitos.

|Requisito|Cómo comprobar y habilitar este requisito|
|-----------------|----------------------------------------------|
|Hyper-V debe estar instalado|Siga las mismas instrucciones que las que se usan [habilitar Hyper-V para el emulador de Windows Phone](/previous-versions/windows/apps/jj863509(v=vs.105)).<br /><br /> Compruebe el estado del servicio **Administración de máquinas virtuales de Hyper-V** en el complemento Servicios.|
|Hyper-V debe estar ejecutándose.|Para obtener más información sobre la administración de servicios, vea los temas siguientes:<br /><br /> -   [Iniciar, detener, pausar, reanudar o reiniciar un servicio](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Configurar cómo se inicia un servicio](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 Debe ser miembro del grupo local Administradores de Hyper-V.

 Para ejecutar el emulador de Visual Studio para Android sin que se le pida continuamente que eleve sus derechos, debe ser miembro del grupo local Administradores de Hyper-V. Si ya es administrador local del equipo cuando instala el SDK, el programa de instalación del SDK lo agrega al grupo Administradores de Hyper-V. En caso contrario, tendrá que habilitar manualmente este requisito.

 Si ejecuta el emulador sin ser miembro del grupo Administradores de Hyper-V, se le pedirá que se una al grupo (el cuadro de diálogo hace referencia en el emulador de Windows Phone). Para unirse al grupo, es necesario tener derechos de administrador.

> [!IMPORTANT]
> Después de unirse al grupo, cierre la sesión o reinicie el equipo para que el cambio surta efecto.

 ![Unión al grupo de seguridad de Administradores de Hyper-V](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")

 Para agregarse a un grupo manualmente, abra el complemento Grupos y usuarios locales.

## <a name="running-the-emulator-from-a-bootable-vhd-is-not-supported"></a>No se admite la ejecución del emulador desde un VHD de arranque
 Si intenta ejecutar una aplicación en el emulador de Visual Studio para Android mientras se ejecuta Windows desde un VHD de arranque, el emulador tardará varios minutos en iniciarse o no se iniciará. Si el emulador no se puede iniciar, verá el mensaje siguiente:  Error al implementar la aplicación. Vuelva a intentarlo.

 Esta configuración no se admite. Para obtener información sobre problemas relacionados, vea [Solución de problemas del emulador de Visual Studio para Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).

## <a name="hyper-v-requires-uncompressed-and-unencrypted-files"></a>Hyper-V requiere archivos no cifrados y sin comprimir
 En un disco duro configurado con el sistema de archivos NTFS, los archivos de disco duro virtual que usa Hyper-V no deben estar comprimidos ni cifrados. Asegúrese de que los siguientes directorios no están comprimidos ni cifrados:

- %localappdata%\Microsoft\XDE

- C:\Archivos de programa (x86)\Microsoft Emulator Manager

- C:\Archivos de programa (x86)\Microsoft Visual Studio Emulator for Android

- %localappdata%\Microsoft\VisualStudioEmulator

En el sistema de archivos ReFS, los archivos de disco duro virtual no deben tener establecido el bit de integridad.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Requisitos de hardware de reenvío de gráficos (compatibilidad con OpenGL ES)

Para que el emulador pueda emular llamadas a la GPU, como las de OpenGL ES, su máquina debe tener una GPU compatible con DirectX que tenga instalados los controladores de DirectX apropiados.

## <a name="see-also"></a>Vea también

- [Solución de problemas del emulador de Visual Studio para Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
