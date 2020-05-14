---
title: Depuración del viaje en el tiempo de máquinas virtuales de Azure en vivo para ASP.NET
description: Obtenga información sobre cómo grabar y reproducir las aplicaciones de ASP.NET en vivo en máquinas virtuales de Azure con Snapshot Debugger.
ms.custom: ''
ms.date: 04/11/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 53dce8b6b468dd5754b5708afccdcbe6cb908d1d
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432218"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Grabar y reproducir aplicaciones de ASP.NET en vivo en máquinas virtuales de Azure con Snapshot Debugger

La versión preliminar de Time Travel Debugging (TTD) en Visual Studio Enterprise proporciona la capacidad de grabar una aplicación web que se ejecuta en una máquina virtual (VM) de Azure y, después, reconstruir y reproducir con precisión la ruta de acceso de ejecución. TTD se integra con Snapshot Debugger y permite rebobinar y reproducir cada línea de código tantas veces como desee, lo que ayudará a aislar e identificar los problemas que podrían producirse en entornos de producción.

La captura de una grabación de TTD no detendrá la aplicación. Sin embargo, la grabación de TDD agrega una sobrecarga significativa al proceso en ejecución, lo que ralentiza el procesamiento en función de factores que incluyen el tamaño del proceso y el número de subprocesos activos.

Esta característica se encuentra en versión preliminar para la versión de Visual Studio 2019 con una licencia Go Live.

En este tutorial va a:

> [!div class="checklist"]
> * Iniciar Snapshot Debugger con Time Travel Debugging habilitado
> * Establecimiento de un punto de instantánea y recopilación de una grabación de viaje en el tiempo
> * Iniciar la depuración de una grabación de viaje en el tiempo

## <a name="prerequisites"></a>Requisitos previos

* Time Travel Debugging para Azure Virtual Machines (VM) solo está disponible para Visual Studio 2019 Enterprise o posterior con la **carga de trabajo de desarrollo de Azure**. (En la pestaña **Componentes individuales**, puede encontrarlo en **Depuración y pruebas** > **Snapshot Debugger**).

    Si aún no está instalado, instale [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Time Travel Debugging está disponible para las siguientes aplicaciones web de Azure VM:
  * Aplicaciones ASP.NET (AMD64) que se ejecutan en .NET Framework 4.8 o versiones posteriores.

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Iniciar Snapshot Debugger con Time Travel Debugging habilitado

1. Abra el proyecto para el que desea recopilar una grabación de viaje en el tiempo.

    > [!IMPORTANT]
    > Para iniciar TTD, abra la *misma versión del código fuente* publicada en el servicio Azure VM.

1. Elija **Depurar > Asociar Snapshot Debugger...** Seleccione la instancia de Azure VM donde se implementó la aplicación web y una cuenta de Azure Storage. Seleccione la opción **Habilitar Time Travel Debugging** en versión preliminar y, después, haga clic en **Adjuntar**.

      ![Seleccione un recurso de Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > La primera vez que selecciona **Asociar Snapshot Debugger** para la máquina virtual, IIS se reinicia automáticamente.

    Los metadatos de los **Módulos** no se activan inicialmente. Vaya a la aplicación web y, después, el botón **Iniciar colección** se activará. Visual Studio ahora está en modo de depuración de instantáneas.

   ![Modo de depuración de instantáneas](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > La extensión de sitio de Application Insights también admite la depuración de instantáneas. Si aparece un mensaje de error "la extensión de sitio no está actualizada", vea las [sugerencias de solución de problemas y los problemas conocidos con la depuración de instantáneas](../debugger/debug-live-azure-apps-troubleshooting.md) para actualizar los detalles.

   En la ventana **Módulos** se muestra cuándo se han cargado todos los módulos para Azure VM (elija **Depurar > Windows > Módulos** para abrir esta ventana).

   ![Comprobación de la ventana Módulos](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Establecimiento de un punto de instantánea y recopilación de una grabación de viaje en el tiempo

1. En el editor de código, haga clic en el medianil izquierdo en un método en el que le interesa establecer un punto de instantánea. Asegúrese de que se trata de código que sabe que se ejecutará.

   ![Definición de un punto de instantánea](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Haga clic con el botón derecho en un icono de punto de instantánea (el círculo hueco) y elija **Acciones**. En la ventana **Configuración de instantáneas**, haga clic en la casilla **Acción**. Después, haga clic en la casilla **Recopilar un seguimiento de viaje en el tiempo hasta el final de este método**.

   ![Recopilar un seguimiento de viaje en el tiempo hasta el final del método](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Haga clic en **Iniciar colección** para activar el punto de instantánea.

   ![Activar el punto de instantánea](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Tomar una instantánea

Cuando se activa un punto de instantánea, este captura una instantánea cada vez que se ejecuta la línea de código donde se coloca el punto de instantánea. Esta ejecución puede derivar de una solicitud real en el servidor. Para forzar que se alcance el punto de instantánea, vaya a la vista del explorador del sitio web y realice las acciones necesarias que provocan que se alcance el punto de instantánea.

## <a name="start-debugging-a-time-travel-recording"></a>Iniciar la depuración de una grabación de viaje en el tiempo

1. Cuando se alcanza el punto de instantánea, aparece una instantánea en la ventana Herramientas de diagnóstico. Para abrir esta ventana, elija **Depurar > Windows > Mostrar herramientas de diagnóstico**.

   ![Apertura de un punto de instantánea](../debugger/media/snapshot-diagsession-window.png)

1. Haga clic en el vínculo Ver instantánea para abrir la grabación de viaje en el tiempo en el editor de código.
  
   Puede ejecutar cada línea de código grabada por TTD con los botones **Continuar** e **Invertir continuar**. Además, se puede usar la barra de herramientas **Depurar** para **Mostrar la instrucción siguiente**, **Paso a paso por instrucciones**, **Paso a paso por procedimientos**, **Paso a paso para salir**, **Paso a paso atrás por instrucciones**, **Paso a paso atrás por procedimientos** y **Paso a paso atrás para salir**.

   ![Iniciar depuración](../debugger/media/time-travel-debugging-step-commands.png)

   También puede usar las ventanas **Locales**, **Inspecciones** y **Pila de llamadas** y evaluar también las expresiones.

   ![Inspección de los datos de instantánea](../debugger/media/time-travel-debugging-start-debugging.png)

    El propio sitio web está todavía activo y los usuarios finales no se ve afectados por ninguna actividad de TTD posterior. Solo se captura una instantánea por cada punto de instantánea de forma predeterminada: una vez que se captura una instantánea, se desactiva el punto de instantánea. Si desea capturar otra instantánea en el punto de instantánea, puede volver a activar el punto de instantánea si hace clic en **Actualizar colección**.

**¿Necesita ayuda?** Consulte las páginas [Solución de problemas y problemas conocidos](../debugger/debug-live-azure-apps-troubleshooting.md) y [Preguntas frecuentes sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Definición de un punto de instantánea condicional

Si es difícil volver a crear un estado determinado en la aplicación, considere si utilizar un punto de instantánea condicional puede resultar útil. Los puntos de instantánea condicionales evitan realizar una recopilación de una grabación de viaje en el tiempo hasta que la aplicación entra en un estado deseado, por ejemplo, cuando una variable tiene un valor concreto que desea inspeccionar. [Puede establecer las condiciones con expresiones, filtros o números de llamadas](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido a recopilar una grabación de viaje en el tiempo para Azure Virtual Machines. Es posible que desee obtener más información sobre Snapshot Debugger.

> [!div class="nextstepaction"]
> [P+F sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)