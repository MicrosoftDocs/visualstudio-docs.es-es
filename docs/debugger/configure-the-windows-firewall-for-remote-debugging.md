---
title: Configurar Firewall de Windows para la depuración remota | Microsoft Docs
ms.date: 10/31/2018
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1fdfb43a00515dff57dd59943043ee0a42dc270f
ms.sourcegitcommit: cdcbf254db737d42275e95de4ffc4f8c14e87e00
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57428731"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Configurar Firewall de Windows para la depuración remota

En una red protegida por el Firewall de Windows, debe configurarse el firewall para permitir la depuración remota. Pruebe Visual Studio y las herramientas de depuración remotas abrir los puertos de firewall adecuados durante la instalación o de inicio, pero también es posible que deba abrir puertos o permitir que las aplicaciones de forma manual.

En este tema se describe cómo configurar el firewall de Windows para habilitar la depuración remota en Windows 10, 8/8.1 y 7; y equipos de Windows Server 2008 R2, 2012 y 2012 R2. El equipo remoto y Visual Studio no tienen que ejecutar el mismo sistema operativo. Por ejemplo, el equipo de Visual Studio puede ejecutar Windows 10 y el equipo remoto puede ejecutar Windows Server 2012 R2.

>[!NOTE]
>Las instrucciones para configurar el firewall de Windows varían ligeramente en diferentes sistemas operativos y las versiones anteriores de Windows. Configuración de Windows 8/8.1, Windows 10 y Windows Server 2012, utilice la palabra *aplicación*, mientras que Windows 7 y Windows Server 2008 usan la palabra *programa*.

## <a name="configure-ports-for-remote-debugging"></a>Configurar puertos para la depuración remota

Visual Studio y el depurador remoto intentan abrir los puertos correctos durante la instalación o de inicio. Sin embargo, en algunos escenarios, como un firewall de terceros, es posible que deba abrir los puertos manualmente.

**Para abrir un puerto:**

1. En Windows **iniciar** menú, busque y abra **Firewall de Windows con seguridad avanzada**. En Windows 10, esto es **Firewall de Windows Defender con seguridad avanzada**.

1. Para un nuevo puerto de entrada, seleccione **reglas de entrada** y, a continuación, seleccione **nueva regla**. Para una regla de salida, seleccione **reglas de salida** en su lugar.

1. En el **entrada Asistente para nueva regla**, seleccione **puerto**y, a continuación, seleccione **siguiente**.

1. Seleccione **TCP** o **UDP**, según el número de puerto de las siguientes tablas.

1. En **puertos locales específicos**, escriba un número de puerto de las siguientes tablas y seleccione **siguiente**.

1. Seleccione **permitir la conexión**y, a continuación, seleccione **siguiente**.

1. Seleccione uno o varios tipos de red para habilitar, incluido el tipo de red para la conexión remota y, a continuación, seleccione **siguiente**.

1. Agregue un nombre para la regla (por ejemplo, **msvsmon**, **IIS**, o **Web Deploy**) y, a continuación, seleccione **finalizar**.

   La nueva regla debería aparecer y se ha seleccionado en el **reglas de entrada** o **reglas de salida** lista.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Puertos en el equipo remoto que habilitan la depuración remota

Para la depuración remota, los siguientes puertos deben estar abiertos en el equipo remoto:

::: moniker range="vs-2017"

|**Puertos**|**Entrante/saliente**|**Protocolo**|**Descripción**|
|-|-|-|-|
|4022|Entrante|TCP|Para VS 2017. El puerto número se incrementa en 2 para cada versión de Visual Studio. Para obtener más información, vea [Asignaciones de puerto de depurador remoto de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4023|Entrante|TCP|Para VS 2017. El puerto número se incrementa en 2 para cada versión de Visual Studio. Este puerto es sólo usa remota depurar un proceso de 32 bits desde una versión de 64 bits del depurador remoto. Para obtener más información, vea [Asignaciones de puerto de depurador remoto de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Saliente|UDP|(Opcional) Se requiere para la detección del depurador remoto.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Puertos**|**Entrante/saliente**|**Protocolo**|**Descripción**|
|-|-|-|-|
|4024|Entrante|TCP|Para VS 2019. El puerto número se incrementa en 2 para cada versión de Visual Studio. Para obtener más información, vea [Asignaciones de puerto de depurador remoto de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4025|Entrante|TCP|Para VS 2019. El puerto número se incrementa en 2 para cada versión de Visual Studio. Este puerto es sólo usa remota depurar un proceso de 32 bits desde una versión de 64 bits del depurador remoto. Para obtener más información, vea [Asignaciones de puerto de depurador remoto de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Saliente|UDP|(Opcional) Se requiere para la detección del depurador remoto.|

::: moniker-end

Si selecciona **usar el modo de compatibilidad administrado** en **herramientas** > **opciones** > **depuración**, abra estos puertos adicionales del depurador remoto. Modo de compatibilidad de depurador administrado permite un heredado, la versión de Visual Studio 2010 del depurador.

|**Puertos**|**Entrante/saliente**|**Protocolo**|**Descripción**|
|-|-|-|-|
|135, 139, 445|Saliente|TCP|Obligatorio.|
|137, 138|Saliente|UDP|Obligatorio.|

Si la directiva de dominio requiere la comunicación de red se realice a través de IPSec, debe abrir puertos adicionales en Visual Studio y los equipos remotos. Para depurar en un servidor web IIS remoto, abra el puerto 80 en el equipo remoto.

|**Puertos**|**Entrante/saliente**|**Protocolo**|**Descripción**|
|-|-|-|-|
|500, 4500|Saliente|UDP|Necesario si la directiva de dominio exige que la comunicación de red se realice a través de IPSec.|
|80|Saliente|TCP|Necesario para la depuración en el servidor web.|

Para permitir que aplicaciones específicas a través del firewall de Windows, consulte [Configurar depuración remota a través de Firewall de Windows](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Configurar la depuración remota a través de firewall de Windows

Puede instalar las herramientas de depuración remotas en el equipo remoto o ejecutarlas desde una carpeta compartida. En cualquier caso, el firewall del equipo remoto debe configurarse correctamente.

En un equipo remoto, las herramientas de depuración remotas se encuentran en:

*\<Directorio de instalación de Visual Studio\>\\Common7\\IDE\\Remote Debugger\\\<x86*, *x64*, o  *AppX*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Permitir y configurar al depurador remoto a través de Firewall de Windows

1. En Windows **iniciar** menú, busque y abra **Windows Firewall**, o **Firewall de Windows Defender**.

1. Seleccione **permitir que una aplicación a través de Firewall de Windows**.

1.  Si **Remote Debugger** o **Visual Studio Remote Debugger** no aparece en **aplicaciones y características permitidas**, seleccione **cambiar la configuración de**y, a continuación, seleccione **permitir otra aplicación**.

1.  Si la aplicación del depurador remoto aún no aparece en el **agregar una aplicación** cuadro de diálogo, seleccione **examinar**y vaya a  *\<directorio de instalación de Visual Studio\> \\Common7\\IDE\\depurador remoto\\\<x86*, *x64*, o *Appx* \> , dependiendo de la arquitectura adecuada para su aplicación. Seleccione *msvsmon.exe*y, a continuación, seleccione **agregar**.

1.  En el **aplicaciones** lista, seleccione el **Remote Debugger** que acaba de agregar. Seleccione **tipos de red**y, a continuación, seleccione uno o varios tipos de red, incluido el tipo de red para la conexión remota.

1.  Seleccione **agregar**y, a continuación, seleccione **Aceptar**.

## <a name="troubleshooting"></a>Solución de problemas de conexión de depuración remota

Si no se puede adjuntar a la aplicación con el depurador remoto, asegúrese de que los puertos del firewall de depuración remota, protocolos, tipos de red y configuración de la aplicación es todos correcta.

- En el Windows **iniciar** menú, busque y abra **Windows Firewall**y seleccione **permitir que una aplicación a través de Firewall de Windows**. Asegúrese de que **Remote Debugger** o **Visual Studio Remote Debugger** aparece en el **aplicaciones y características permitidas** una lista con una casilla activada y los tipos de red correcta seleccionado. Si no es así, [agregar la configuración y las aplicaciones correctas](#configure-remote-debugging-through-windows-firewall).

- En el Windows **iniciar** menú, busque y abra **Firewall de Windows con seguridad avanzada**. Asegúrese de que **Remote Debugger** o **Visual Studio Remote Debugger** aparece bajo **reglas de entrada** (y, opcionalmente, **reglas de salida**) con un icono de marca de verificación verde y que todas las configuraciones son correctas.

  - Para ver o cambiar la configuración de reglas, haga clic en el **Remote Debugger** aplicación en la lista y seleccione **propiedades**. Use la **propiedades** pestañas para habilitar o deshabilitar la regla o cambiar el puerto números, protocolos o tipos de red.
  - Si la aplicación del depurador remoto no aparece en la lista de reglas, [agregar y configurar los puertos correctos](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>Vea también

- [Depuración remota](../debugger/remote-debugging.md)
- [Asignaciones de puerto de depurador remoto de Visual Studio](../debugger/remote-debugger-port-assignments.md)
