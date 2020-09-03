---
title: Depuración de aplicaciones de Azure de ASP.NET en vivo
description: Obtenga información sobre cómo establecer puntos de instantánea y ver las instantáneas con Snapshot Debugger.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 07ebe8a583717689ca424bf969e7c19e87ebf08e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350672"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Depuración de aplicaciones de Azure de ASP.NET en vivo con Snapshot Debugger

Snapshot Debugger toma una instantánea de las aplicaciones en producción cuando se ejecuta el código que le interesa. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

Los puntos de instantánea y los puntos de registro son similares a los puntos de interrupción, pero a diferencia de estos últimos, los puntos de instantánea no detienen la aplicación cuando se alcanzan dichos puntos. Normalmente, la captura de una instantánea en un punto de instantánea tarda 10-20 milisegundos.

En este tutorial va a:

> [!div class="checklist"]
> * Iniciar Snapshot Debugger
> * Establecer un punto de instantánea y ver una instantánea
> * Establecer un punto de registro

## <a name="prerequisites"></a>Requisitos previos

* Snapshot Debugger solo está disponible a partir de Visual Studio 2017 Enterprise, versión 15.5 o posteriores, con la **carga de trabajo de desarrollo de Azure**. (En la pestaña **Componentes individuales**, puede encontrarlo en **Depuración y pruebas** > **Snapshot Debugger**).

   ::: moniker range=">=vs-2019"
   Si aún no está instalado, instale [Visual Studio 2019](https://visualstudio.microsoft.com/downloads). Si realiza la actualización desde una instalación anterior de Visual Studio, ejecute el Instalador de Visual Studio y compruebe el componente de Snapshot Debugger en la **carga de trabajo de desarrollo de ASP.NET y web**.
   ::: moniker-end
   ::: moniker range="<=vs-2017"
   Si aún no está instalado, instale [Visual Studio 2017 Enterprise, versión 15.5](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) o posterior. Si realiza la actualización desde una instalación anterior de Visual Studio 2017, ejecute el Instalador de Visual Studio y compruebe el componente de Snapshot Debugger en la **carga de trabajo de desarrollo de ASP.NET y web**.
   ::: moniker-end

* Plan de Azure App Service básico o superior.

* La colección de instantáneas está disponible para las siguientes aplicaciones web que se ejecutan en Azure App Service:
  * Aplicaciones ASP.NET que se ejecutan en .NET Framework 4.6.1 o versiones posteriores.
  * Aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.0 o posteriores en Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Apertura del proyecto e inicio de Snapshot Debugger

1. Abra el proyecto de cuya depuración desea realizar una instantánea.

   > [!IMPORTANT]
   > Para realizar una instantánea de la depuración, abra la *misma versión del código fuente* publicada en Azure App Service.

::: moniker range="<=vs-2017"

2. En Cloud Explorer (**Ver > Cloud Explorer**), haga clic con el botón derecho en la instancia de Azure App Service en la que se implementó el proyecto y seleccione **Asociar Snapshot Debugger**.

   ![Iniciar Snapshot Debugger](../debugger/media/snapshot-launch.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Elija **Depurar > Asociar Snapshot Debugger...** Seleccione la instancia de Azure App Service en la que se implementó el proyecto y una cuenta de Azure Storage y, a continuación, haga clic en **Adjuntar**. Snapshot Debugger también admite [Azure Kubernetes Service](debug-live-azure-kubernetes.md) y [Azure Virtual Machines (VM) y Virtual Machine Scale Sets](debug-live-azure-virtual-machines.md).

   ![Inicio de Snapshot Debugger desde el menú Depurar](../debugger/media/snapshot-debug-menu-attach.png)

   ![Seleccione un recurso de Azure](../debugger/media/snapshot-select-azure-resource-appservices.png)

::: moniker-end

   > [!IMPORTANT]
   > La primera vez que selecciona **Asociar Snapshot Debugger**, se le pide que instale la extensión de sitio de Snapshot Debugger en la instancia de Azure App Service. Esta instalación requiere un reinicio de Azure App Service.

   ::: moniker range="<=vs-2017"
   > [!NOTE]
   > La extensión de sitio de Application Insights también admite la depuración de instantáneas. Si aparece un mensaje de error "la extensión de sitio no está actualizada", vea las [sugerencias de solución de problemas y los problemas conocidos con la depuración de instantáneas](../debugger/debug-live-azure-apps-troubleshooting.md) para actualizar los detalles.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   > [!NOTE]
   > (Visual Studio 2019 versión 16.2 y posterior) Snapshot Debugger ha habilitado la compatibilidad en la nube de Azure. Asegúrese de que el recurso de Azure y la cuenta de Azure Storage que seleccione pertenecen a la misma nube. Póngase en contacto con su administrador de Azure si tiene alguna pregunta sobre las configuraciones de [cumplimiento de Azure](https://azure.microsoft.com/overview/trusted-cloud/) de su empresa.
   ::: moniker-end

   Visual Studio ahora está en modo de depuración de instantáneas.
   ![Modo de depuración de instantáneas](../debugger/media/snapshot-message.png)

   En la ventana **Módulos** se muestra cuándo se han cargado todos los módulos para Azure App Service (elija **Depurar > Windows > Módulos** para abrir esta ventana).

   ![Comprobación de la ventana Módulos](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Definición de un punto de instantánea

1. En el editor de código, haga clic en el medianil izquierdo junto a una línea de código en la que le interesa establecer un punto de instantánea. Asegúrese de que se trata de código que sabe que se ejecutará.

   ![Definición de un punto de instantánea](../debugger/media/snapshot-set-snappoint.png)

2. Haga clic en **Iniciar colección** para activar el punto de instantánea.

   ![Activar el punto de instantánea](../debugger/media/snapshot-start-collection.png)

   > [!TIP]
   > No puede detenerse al visualizar una instantánea, pero puede colocar varios puntos de instantánea en el código para seguir la ejecución en diferentes líneas de código. Si tiene varios puntos de instantánea en el código, Snapshot Debugger garantiza que las instantáneas correspondientes sean de la misma sesión de usuario final. Snapshot Debugger hace esto aunque muchos usuarios visiten la aplicación.

## <a name="take-a-snapshot"></a>Tomar una instantánea

Una vez que se establece un punto de instantánea, puede generar manualmente una instantánea yendo a la vista de explorador del sitio web y ejecutando la línea de código marcada o esperar a que los usuarios generen una a partir de su uso del sitio.

## <a name="inspect-snapshot-data"></a>Inspección de los datos de instantánea

1. Cuando se alcanza el punto de instantánea, aparece una instantánea en la ventana Herramientas de diagnóstico. Para abrir esta ventana, elija **Depurar > Windows > Mostrar herramientas de diagnóstico**.

   ![Apertura de un punto de instantánea](../debugger/media/snapshot-diagsession-window.png)

1. Haga doble clic en el punto de instantánea para abrir la instantánea en el editor de código.

   ![Inspección de los datos de instantánea](../debugger/media/snapshot-inspect-data.png)

   Desde esta vista, puede mantener el puntero sobre las variables para ver información sobre datos, usar las ventanas **Variables locales**, **Inspecciones** y **Pila de llamadas** y también evaluar expresiones.

   El propio sitio web está todavía activo y los usuarios finales no se ven afectados. Solo se captura una instantánea por cada punto de instantánea de forma predeterminada: una vez que se captura una instantánea, se desactiva el punto de instantánea. Si desea capturar otra instantánea en el punto de instantánea, puede volver a activar el punto de instantánea si hace clic en **Actualizar colección**.

También puede agregar más puntos de instantánea a la aplicación y activarlos con el botón **Actualizar colección**.

**¿Necesita ayuda?** Consulte las páginas [Solución de problemas y problemas conocidos](../debugger/debug-live-azure-apps-troubleshooting.md) y [Preguntas frecuentes sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Definición de un punto de instantánea condicional

Si es difícil volver a crear un estado determinado en la aplicación, considere la posibilidad de utilizar un punto de instantánea condicional. Los puntos de instantánea condicionales ayudan a controlar cuándo hacer una instantánea, por ejemplo, cuando una variable contiene un valor concreto que desea inspeccionar. Puede establecer las condiciones con expresiones, filtros o números de llamadas.

#### <a name="to-create-a-conditional-snappoint"></a>Para crear un punto de instantánea condicional

1. Haga clic con el botón derecho en un icono de punto de instantánea (el círculo hueco) y elija **Configuración**.

   ![Selección de Configuración](../debugger/media/snapshot-snappoint-settings.png)

1. En la ventana de configuración del punto de instantánea, escriba una expresión.

   ![Escribir una expresión](../debugger/media/snapshot-snappoint-conditions.png)

   En la ilustración anterior, la instantánea solo se realiza para el punto de instantánea cuando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Establecer un punto de registro

Además de realizar una instantánea cuando se alcanza un punto de instantánea, también puede configurar un punto de instantánea para registrar un mensaje (es decir, crear un punto de registro). Puede establecer puntos de registro sin tener que volver a implementar la aplicación. Los puntos de registro se ejecutan de forma práctica y no causan ningún impacto o efecto secundario en la aplicación en ejecución.

#### <a name="to-create-a-logpoint"></a>Para crear un punto de registro

1. Haga clic con el botón derecho en un icono de punto de instantánea (el hexágono azul) y elija **Configuración**.

1. En la ventana de configuración del punto de instantánea, seleccione **Acciones**.

   ![Creación de un punto de registro](../debugger/media/snapshot-logpoint.png)

1. En el campo **mensaje**, puede escribir el nuevo mensaje de registro que desea registrar. También puede evaluar las variables del mensaje de registro si se colocan entre llaves.

   Si elige **Se envía a la ventana de salida**, cuando se alcanza el punto de registro, el mensaje aparece en la ventana Herramientas de diagnóstico.

   ![Datos del punto de registro en la ventana Herramientas de diagnóstico](../debugger/media/snapshot-logpoint-output.png)

   Si elige **Se envía al registro de aplicaciones**, cuando se alcanza el punto de registro, el mensaje aparece en cualquier lugar en el que puede ver los mensajes de `System.Diagnostics.Trace`, o `ILogger` en .NET Core, como [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido cómo utilizar Snapshot Debugger para App Services. Es posible que desee obtener más información sobre esta característica.

> [!div class="nextstepaction"]
> [P+F sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)