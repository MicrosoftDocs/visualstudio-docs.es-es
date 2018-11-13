---
title: Uso de Visual Studio asistente Publicar aplicación de Azure | Microsoft Docs
description: Aprenda a configurar las distintas configuraciones en Visual Studio publicar Azure Application Wizard
author: ghogen
manager: douge
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: c9c4104d4d07cab7486038a8787ed0c7759abd60
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002966"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Uso del asistente Publicar aplicación de Azure de Visual Studio

Después de desarrollar una aplicación web en Visual Studio, puede publicar dicha aplicación en un servicio de nube de Azure mediante el **publicar aplicación de Azure** asistente.

> [!Note]
> En este artículo es sobre la implementación de servicios en la nube, no en sitios web. Para obtener información sobre la implementación en sitios web, consulte [cómo implementar un sitio Web de Azure](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Tener acceso al asistente Publicar aplicación de Azure

Se puede acceder al asistente Publicar aplicación de Azure de dos maneras, según el tipo de proyecto de Visual Studio que tiene.

**Si tiene un proyecto de servicio de nube de Azure:**

1. Cree o abra un proyecto de servicio de nube de Azure en Visual Studio.

1. En **el Explorador de soluciones**, haga clic en el proyecto y, en el menú contextual, seleccione **publicar**.

**Si tiene un proyecto de aplicación web que no está habilitado para Azure:**

1. Cree o abra un proyecto de servicio de nube de Azure en Visual Studio.

1. En **el Explorador de soluciones**, haga clic en el proyecto y, en el menú contextual, seleccione **convertir** > **convertir en proyecto de servicio en la nube de Azure**. 

1. En **el Explorador de soluciones**, haga clic en el proyecto de Azure recién creado y, en el menú contextual, seleccione **publicar**.

## <a name="sign-in-page"></a>Página de inicio de sesión

![Página de inicio de sesión](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Cuenta** : seleccione una cuenta o seleccione **agregar una cuenta** en la lista desplegable de cuenta.

**Elija su suscripción** : elija la suscripción que se usará para la implementación.

## <a name="settings-page---common-settings-tab"></a>Página de configuración: pestaña Configuración común

![Configuración común](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Servicio en la nube** -mediante la lista desplegable, seleccione una existente en la nube, servicio o seleccione  **&lt;crear nuevo >** y crear un servicio en la nube. El centro de datos aparece entre paréntesis para cada servicio en la nube. Se recomienda que los datos de ubicación del centro de servicio en la nube sea la misma ubicación del centro de datos para la cuenta de almacenamiento (configuración avanzada).

**Entorno** -seleccione **producción** o **ensayo**. Elija el entorno de ensayo si desea implementar la aplicación en un entorno de prueba. 

**Configuración de compilación** -seleccione **depurar** o **versión**.

**Configuración del servicio** -seleccione **en la nube** o **Local**.

**Habilitar Escritorio remoto para todos los roles** : seleccione esta opción si desea poder conectarse de forma remota al servicio. Esta opción se utiliza principalmente para solucionar problemas. Para obtener más información, consulte [Habilitar conexión a Escritorio remoto para un rol en Azure Cloud Services mediante Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Habilitar Web Deploy para todos los roles web** : seleccione esta opción para habilitar la implementación web para el servicio. También debe seleccionar la **habilitar Escritorio remoto para todos los roles** opción para usar esta característica. Para obtener más información, consulte [publicar un servicio en la nube con Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Página de configuración: pestaña Opciones avanzada

![Configuración avanzada](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Etiqueta de implementación** -acepte el nombre predeterminado o escriba un nombre de su elección. Para anexar la fecha a la etiqueta de implementación, deje activada la casilla de verificación. 

**Cuenta de almacenamiento** -seleccione la cuenta de almacenamiento que se usará para esta implementación, **&lt;crear nuevo > para crear una cuenta de almacenamiento. El centro de datos aparece entre paréntesis para cada cuenta de almacenamiento. Se recomienda que la ubicación del centro de datos para la cuenta de almacenamiento es el mismo que la ubicación del centro de datos para el servicio en la nube (configuración común).

La cuenta de almacenamiento de Azure almacena el paquete para la implementación de aplicaciones. Una vez implementada la aplicación, se quita el paquete de la cuenta de almacenamiento.

**Eliminar implementación en caso de error** : seleccione esta opción para que la implementación puede eliminar si se encuentra algún error durante la publicación. Esto debería ser desactivada si desea mantener una dirección IP virtual constante para el servicio en la nube.

**Actualización de implementación** : seleccione esta opción si desea implementar solo los componentes actualizados. Este tipo de implementación puede ser más rápido que una implementación completa. Esto se debe comprobar si desea mantener una dirección IP virtual constante para el servicio en la nube. 

**Actualización de implementación - configuración** : este cuadro de diálogo se usa para especificar cómo desea que se actualicen los roles. Si elige **actualización Incremental**, cada instancia de la aplicación se actualiza una tras otra, para que la aplicación siempre esté disponible. Si elige **actualización simultánea**, todas las instancias de la aplicación se actualizan al mismo tiempo. La actualización simultánea es más rápida, pero el servicio no esté disponible durante el proceso de actualización.

![Configuración de implementación](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**Habilitar IntelliTrace** : especifique si desea habilitar IntelliTrace. Con IntelliTrace, puede registrar información de depuración amplia para una instancia de rol cuando se ejecuta en Azure. Si necesita encontrar la causa de un problema, puede usar los registros de IntelliTrace para recorrer el código de Visual Studio como si se estuviera ejecutando en Azure. Para obtener más información sobre el uso de IntelliTrace, vea [depurar un servicio en la nube de Azure publicado con Visual Studio e IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Habilitar generación de perfiles** : especifique si desea habilitar la generación de perfiles de rendimiento. El generador de perfiles de Visual Studio le permite obtener un análisis exhaustivo de los aspectos de cálculo de cómo se ejecuta el servicio en la nube. Para obtener más información acerca de cómo utilizar el generador de perfiles de Visual Studio, consulte [probar el rendimiento de un servicio de nube de Azure](./vs-azure-tools-performance-profiling-cloud-services.md).

**Habilitar Remote Debugger para todos los roles** : especifique si desea habilitar la depuración remota. Para obtener más información sobre la depuración de servicios en la nube con Visual Studio, consulte [depuración de una máquina virtual en Visual Studio o un servicio de nube de Azure](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Página Configuración de diagnóstico

![Configuración de diagnóstico](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Diagnósticos le permite solucionar problemas de un servicio de nube de Azure (o máquina virtual de Azure). Para obtener información acerca de los diagnósticos, consulte [configurar diagnósticos para Azure Cloud Services y Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Para obtener información acerca de Application Insights, consulte [¿qué es Application Insights?](/azure/application-insights/app-insights-overview.md).

## <a name="summary-page"></a>Página de resumen

![Resumen](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Perfil de destino** -puede elegir crear un perfil de publicación de la configuración que ha elegido. Por ejemplo, podría crear un perfil para un entorno de prueba y otro para producción. Para guardar este perfil, elija el **guardar** icono. El asistente crea el perfil y lo guarda en el proyecto de Visual Studio. Para modificar el nombre del perfil, abra el **perfil objetivo** lista y, a continuación, elija  **&lt;administrar... &gt;**.

   > [!Note]
   > El perfil de publicación aparece en el Explorador de soluciones en Visual Studio, y la configuración del perfil se escribe en un archivo con una extensión .azurePubxml. Configuración se guarda como atributos de etiquetas XML.

## <a name="publishing-your-application"></a>Publicación de la aplicación

Una vez que configure toda la configuración de la implementación del proyecto, seleccione **publicar** en la parte inferior del cuadro de diálogo. Puede supervisar el estado del proceso en el **salida** ventana de Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

- [Migrar y publicar una aplicación Web a un servicio de nube de Azure desde Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Aprenda a usar Visual Studio para publicar un servicio de nube de Azure](./vs-azure-tools-publishing-a-cloud-service.md)

- [Depurar un servicio en la nube de Azure publicado con Visual Studio e IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Probar el rendimiento de un servicio de nube de Azure](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Configuración de diagnósticos para Azure Cloud Services y máquinas virtuales](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [¿Qué es Application Insights?](/azure/application-insights/app-insights-overview.md)