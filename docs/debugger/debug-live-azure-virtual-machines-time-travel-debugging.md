---
title: Tiempo viaje depuración ASP.NET Azure máquinas virtuales en vivo
description: Obtenga información sobre cómo grabar y reproducir las aplicaciones ASP.NET activas en Azure virtual machines con el depurador de instantáneas.
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
ms.openlocfilehash: 3a81f6aa138b361a44a272ebda3557d27a914c64
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854156"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>La grabación y reproducción de las aplicaciones ASP.NET activas en Azure virtual machines con el depurador de instantáneas

La vista previa de depuración de viaje de tiempo (TTD) en Visual Studio Enterprise proporciona la capacidad de registrar una aplicación Web que se ejecuta en una máquina Virtual de Azure (VM) y, a continuación, con precisión reconstruir y reproducir la ruta de acceso de ejecución. TTD se integra con el depurador de instantáneas y rebobinar y reproducir cada línea de código permite a cualquier número de veces que desea, puede ayudar a aislar e identificar los problemas que podrían producirse solo en entornos de producción.

Capturar una grabación TTD no detendrá la aplicación. Sin embargo, la grabación de TDD agrega una sobrecarga considerable para el proceso en ejecución, se ralentiza en función de factores como el tamaño de proceso y el número de subprocesos activos.

Esta característica está en versión preliminar para la versión de Visual Studio de 2019 con una licencia go live.

En este tutorial va a:

> [!div class="checklist"]
> * Iniciar al depurador de instantáneas con la depuración en tiempo de viaje habilitado
> * Establezca un punto de acoplamiento y recopilar un tiempo de viaje grabación
> * Inicie la depuración de un tiempo de viaje grabación

## <a name="prerequisites"></a>Requisitos previos

* Depuración en tiempo de viaje para Azure Virtual Machines (VM) solo está disponible para Visual Studio 2019 Enterprise o posterior con el **carga de trabajo de desarrollo de Azure**. (En la pestaña **Componentes individuales**, puede encontrarlo en **Depuración y pruebas** > **Snapshot Debugger**).

    Si aún no está instalado, instale [Visual Studio Enterprise de 2019](https://visualstudio.microsoft.com/vs/).

* Depuración en tiempo de desplazamiento está disponible para las siguientes aplicaciones web de máquina virtual de Azure:
  * Aplicaciones de ASP.NET (AMD64) que se ejecutan en .NET Framework 4.8 o posterior.

## <a name="open-your-project-and-start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Abra el proyecto e iniciar al depurador de instantáneas con la depuración en tiempo de viaje habilitado

1. Abra el proyecto para que gustaría recopilar un tiempo de grabación de viaje.

    > [!IMPORTANT]
    > Para empezar a TTD, deberá abrir el *misma versión de código fuente* que se publica en el servicio de máquina virtual de Azure.

1. Elija **Depurar > Asociar Snapshot Debugger...** Seleccione la aplicación web se implementa en la máquina virtual de Azure y una cuenta de almacenamiento de Azure. Seleccione el **habilitar la depuración en tiempo de viaje** opción de vista previa y, a continuación, haga clic en **adjuntar**.

      ![Seleccione un recurso de Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > La primera vez que selecciona **Asociar Snapshot Debugger** para la máquina virtual, IIS se reinicia automáticamente.

    Los metadatos para el **módulos** no se activa inicialmente. Vaya a la aplicación web y la **iniciar colección** botón a continuación, se vuelve activo. Visual Studio ahora está en modo de depuración de instantáneas.

   ![Modo de depuración de instantáneas](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > La extensión de sitio de Application Insights también admite la depuración de instantáneas. Si aparece un mensaje de error "la extensión de sitio no está actualizada", vea las [sugerencias de solución de problemas y los problemas conocidos con la depuración de instantáneas](../debugger/debug-live-azure-apps-troubleshooting.md) para actualizar los detalles.

   El **módulos** ventana muestra cuándo se cargan todos los módulos de la máquina virtual de Azure (elija **Depurar > Windows > módulos** para abrir esta ventana).

   ![Comprobación de la ventana Módulos](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Establezca un punto de acoplamiento y recopilar un tiempo de viaje grabación

1. En el editor de código, haga clic en el margen interno izquierdo de un método que le interese para establecer un punto de acoplamiento. Asegúrese de que se trata de código que sabe que se ejecutará.

   ![Definición de un punto de instantánea](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Haga clic en el icono de punto de acoplamiento (la bola hueco) y elija **acciones**. En el **configuración instantáneas** ventana, haga clic en el **acción** casilla de verificación. A continuación, haga clic en el **recopilar un seguimiento del desplazamiento de tiempo hasta el final de este método** casilla de verificación.

   ![Recopilar un seguimiento del desplazamiento de tiempo hasta el final del método](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Haga clic en **Iniciar colección** para activar el punto de instantánea.

   ![Activar el punto de instantánea](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Tomar una instantánea

Cuando se activa un punto de acoplamiento, captura una instantánea cada vez que ejecuta la línea de código donde se coloca el punto de acoplamiento. Esta ejecución puede deberse a una solicitud real en el servidor. Para forzar que se alcance el punto de instantánea, vaya a la vista del explorador del sitio web y realice las acciones necesarias que provocan que se alcance el punto de instantánea.

## <a name="start-debugging-a-time-travel-recording"></a>Inicie la depuración de un tiempo de viaje grabación

1. Cuando se alcanza el punto de instantánea, aparece una instantánea en la ventana Herramientas de diagnóstico. Para abrir esta ventana, elija **Depurar > Windows > Mostrar herramientas de diagnóstico**.

   ![Apertura de un punto de instantánea](../debugger/media/snapshot-diagsession-window.png)

1. Haga clic en el vínculo de instantánea de la vista para abrir el desplazamiento de tiempo grabación en el editor de código.
  
   Puede ejecutar todas las líneas de código que se graba el TTD mediante el uso de la **continuar** y **invertir continuar** botones. Además, el **depurar** se puede usar para la barra de herramientas **mostrar la instrucción siguiente**, **paso a paso**, **saltar**, **paso a paso fuera**, **Paso nuevo en**, **Saltar atrás**, **revertir paso**.

   ![Iniciar depuración](../debugger/media/time-travel-debugging-step-commands.png)

   También puede usar el **variables locales**, **inspecciones**, y **pila de llamadas** windows y también evaluar expresiones.

   ![Inspección de los datos de instantánea](../debugger/media/time-travel-debugging-start-debugging.png)

    El mismo sitio Web está todavía activo y los usuarios finales no están afectados por las actividades posteriores de TTD. Solo se captura una instantánea por cada punto de instantánea de forma predeterminada: una vez que se captura una instantánea, se desactiva el punto de instantánea. Si desea capturar otra instantánea en el punto de instantánea, puede volver a activar el punto de instantánea si hace clic en **Actualizar colección**.

**¿Necesita ayuda?** Consulte las páginas [Solución de problemas y problemas conocidos](../debugger/debug-live-azure-apps-troubleshooting.md) y [Preguntas frecuentes sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Definición de un punto de instantánea condicional

Si es difícil volver a crear un estado determinado en la aplicación, considere si utilizar un punto de instantánea condicional puede resultar útil. Ayuda de puntos de acoplamiento condicional que evitar la recopilación de un tiempo de viaje grabación hasta que la aplicación entra en un estado deseado, por ejemplo, cuando una variable tiene un valor concreto que desea inspeccionar. [Puede establecer las condiciones de uso de expresiones, los filtros, o el número de visitas](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido cómo recopilar un viaje de tiempo grabación para Azure Virtual Machines. Es posible que desee Obtenga más información sobre Snapshot Debugger.

> [!div class="nextstepaction"]
> [P+F sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)