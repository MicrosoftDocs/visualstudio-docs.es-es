---
title: Configuración del Firewall de Windows para la depuración remota | Microsoft Docs
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fa5d60d7fe662cff31b54bf3a13c203f4b6d8c9
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350698"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Configuración del Firewall de Windows para la depuración remota

En una red protegida por el Firewall de Windows, hay que configurar el firewall para permitir la depuración remota. Visual Studio y las herramientas de depuración remota intentan abrir los puertos de firewall correctos durante la instalación o el inicio, pero es posible que también tenga que abrir puertos o permitir las aplicaciones de forma manual.

En este tema se describe cómo configurar el Firewall de Windows para habilitar la depuración remota en equipos con Windows 10, 8/8.1 y 7, y con Windows Server 2012 R2, 2012 y 2008 R2. Visual Studio y el equipo remoto no tienen por qué ejecutar el mismo sistema operativo. Por ejemplo, el equipo de Visual Studio puede ejecutar Windows 10 y el equipo remoto puede ejecutar Windows Server 2012 R2.

>[!NOTE]
>Las instrucciones para configurar el firewall de Windows varían ligeramente en los distintos sistemas operativos y para versiones más antiguas de Windows. La configuración de Windows 8/8.1, Windows 10 y Windows Server 2012 usa la palabra *aplicación*, mientras que Windows 7 y Windows Server 2008 usan la palabra *programa*.

## <a name="configure-ports-for-remote-debugging"></a>Para configurar puertos para la depuración remota

Visual Studio y el depurador remoto intentan abrir los puertos correctos durante la instalación o el inicio. Aunque en algunos escenarios, como un firewall de terceros, puede que tenga que abrir los puertos manualmente.

**Para abrir un puerto:**

1. En el menú **Inicio** de Windows, busque **Firewall de Windows con seguridad avanzada** y ábralo. En Windows 10, esta opción se llama **Firewall de Windows Defender con seguridad avanzada**.

1. Para un nuevo puerto entrante, seleccione **Reglas de entrada** y, después, elija **Nueva regla**. En el caso de una regla de salida, seleccione **Reglas de salida**.

1. En el **Asistente para nueva regla de entrada**, seleccione **Puerto** y luego elija **Siguiente**.

1. Seleccione **TCP** o **UDP**, según el número de puerto de las tablas siguientes.

1. En **Puertos locales específicos**, escriba un número de puerto de estas tablas y seleccione **Siguiente**.

1. Seleccione **Permitir la conexión** y, después, seleccione **Siguiente**.

1. Seleccione uno o más tipos de red para habilitarlos, incluido el tipo de red para la conexión remota y, después, seleccione **Siguiente**.

1. Agregue un nombre para la regla (por ejemplo, **msvsmon**, **IIS** o **Web Deploy**) y, después, seleccione **Finalizar**.

   Aparecerá la nueva regla, que podrá seleccionar en la lista **Reglas de entrada** o **Reglas de salida**.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Puertos en el equipo remoto que habilitan la depuración remota

Para la depuración remota, los siguientes puertos deben estar abiertos en el equipo remoto:

::: moniker range="vs-2017"

|**Puertos**|**Entrante/saliente**|**Protocolo**|**Descripción**|
|-|-|-|-|
|4022|Entrante|TCP|Para VS 2017. El número de puerto se incrementa en 2 para cada versión de Visual Studio. Para obtener más información, vea [Asignaciones de puerto de depurador remoto de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4023|Entrante|TCP|Para VS 2017. El número de puerto se incrementa en 2 para cada versión de Visual Studio. Este puerto solo se usa para depurar de forma remota un proceso de 32 bits desde una versión de 64 bits del depurador remoto. Para obtener más información, vea [Asignaciones de puerto de depurador remoto de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Saliente|UDP|(Opcional) Necesario para la detección del depurador remoto.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Puertos**|**Entrante/saliente**|**Protocolo**|**Descripción**|
|-|-|-|-|
|4024|Entrante|TCP|Para VS 2019. El número de puerto se incrementa en 2 para cada versión de Visual Studio. Para obtener más información, vea [Asignaciones de puerto de depurador remoto de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4025|Entrante|TCP|Para VS 2019. El número de puerto se incrementa en 2 para cada versión de Visual Studio. Este puerto solo se usa para depurar de forma remota un proceso de 32 bits desde una versión de 64 bits del depurador remoto. Para obtener más información, vea [Asignaciones de puerto de depurador remoto de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Saliente|UDP|(Opcional) Necesario para la detección del depurador remoto.|

::: moniker-end

Si selecciona **Usar el modo de compatibilidad administrado** en **Herramientas** > **Opciones** > **Depuración**, abra estos puertos adicionales del depurador remoto. El modo de compatibilidad administrado del depurador habilita una versión heredada del depurador de Visual Studio 2010.

|**Puertos**|**Entrante/saliente**|**Protocolo**|**Descripción**|
|-|-|-|-|
|135, 139, 445|Saliente|TCP|Obligatorio.|
|137, 138|Saliente|UDP|Obligatorio.|

Si para la directiva de dominio es necesario que la comunicación de red se realice a través de IPSec, debe abrir puertos adicionales en Visual Studio y en los equipos remotos. Para depurar en un servidor web de IIS remoto, abra el puerto 80 en el equipo remoto.

|**Puertos**|**Entrante/saliente**|**Protocolo**|**Descripción**|
|-|-|-|-|
|500, 4500|Saliente|UDP|Necesario si la directiva de dominio exige que la comunicación de red se realice a través de IPSec.|
|80|Saliente|TCP|Necesario para la depuración en el servidor web.|

Para permitir aplicaciones específicas a través del firewall de Windows, vea [Configurar la depuración remota a través de Firewall de Windows](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Configurar la depuración remota a través de Firewall de Windows

Puede instalar las herramientas de depuración remota en el equipo remoto o ejecutarlas desde una carpeta compartida. En cualquier caso, el firewall del equipo remoto debe estar configurado correctamente.

En un equipo remoto, las herramientas de depuración remota se encuentran en:

*\<Visual Studio installation directory\>\\Common7\\IDE\\Depurador remoto\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Permitir y configurar el depurador remoto a través de Firewall de Windows

1. En el menú **Inicio** de Windows, busque **Firewall de Windows** o **Firewall de Windows Defender** y ábralo.

1. Seleccione **Permitir una aplicación a través de Firewall de Windows**.

1. Si **Depurador remoto** o **Visual Studio Remote Debugger** no aparece en **Aplicaciones y características permitidas**, seleccione **Cambiar configuración** y, después, elija **Permitir otra aplicación**.

1. Si la aplicación de depurador remoto todavía no aparece en el cuadro de diálogo **Agregar una aplicación**, seleccione **Examinar** y vaya a **\<Visual Studio installation directory\>\\Common7\\IDE\\Depurador remoto\\\<x86*, *x64*, or *Appx*\>, en función de la arquitectura adecuada para la aplicación. Seleccione *msvsmon.exe* y, después, elija **Agregar**.

1. En la lista **Aplicaciones**, seleccione el **Depurador remoto** que acaba de agregar. Seleccione **Tipos de red** y elija uno o más tipos de red, incluido el tipo de red para la conexión remota.

1. Seleccione **Agregar** y luego **Aceptar**.

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>Solución de problemas de conexión de depuración remota

Si no puede conectarse a la aplicación con el depurador remoto, compruebe que los puertos de firewall de depuración remota, los protocolos, los tipos de red y la configuración de la aplicación son correctos.

- En el menú **Inicio** de Windows, busque y abra **Firewall de Windows** y seleccione **Permitir una aplicación a través de Firewall de Windows**. Asegúrese de que **Depurador remoto** o **Visual Studio Remote Debugger** aparecen seleccionados en la **Lista de aplicaciones y características permitidas** y que están seleccionados los tipos de red correctos. De no ser así [agregue las aplicaciones y la configuración correctas](#configure-remote-debugging-through-windows-firewall).

- En el menú **Inicio** de Windows, busque **Firewall de Windows con seguridad avanzada** y ábralo. Asegúrese de que **Depurador remoto** o **Visual Studio Remote Debugger** aparecen en **Reglas de entrada** (o bien en **Reglas de salida**) con un icono de marca de verificación verde y que todos los valores son correctos.

  - Para ver o cambiar la configuración de la regla, haga clic con el botón derecho en la aplicación **Depurador remoto** de la lista y seleccione **Propiedades**. Use las pestañas **Propiedades** para habilitar o deshabilitar la regla, o cambiar los números de puerto, los protocolos o los tipos de red.
  - Si la aplicación de depurador remoto no aparece en la lista de reglas, [agregue y configure los puertos correctos](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>Vea también

- [Depuración remota](../debugger/remote-debugging.md)
- [Asignaciones de puerto del depurador remoto de Visual Studio](../debugger/remote-debugger-port-assignments.md)
