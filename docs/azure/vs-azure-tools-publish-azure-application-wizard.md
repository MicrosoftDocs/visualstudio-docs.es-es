---
title: Publicación de un servicio en la nube de Azure
description: Obtenga información sobre cómo configurar los distintos ajustes del Asistente Publicar aplicación de Azure de Visual Studio
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 87082a0d4df4542f36b1ce95cba92d261a2b4d9e
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902316"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Uso del Asistente Publicar aplicación de Azure de Visual Studio

Después de desarrollar una aplicación web en Visual Studio, puede publicarla en un servicio en la nube de Azure mediante el asistente **Publicar aplicación de Azure** .

> [!Note]
> En este artículo se explica la implementación en servicios en la nube pero no en sitios web. Para obtener más información sobre la implementación en sitios web, consulte [Implementación de un sitio web de Azure](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Acceso al Asistente Publicar aplicación de Azure

Puede tener acceso al Asistente Publicar aplicación de Azure de dos formas según el tipo de proyecto de Visual Studio que tiene.

**Si tiene un proyecto de servicio en la nube de Azure:**

1. Cree o abra un proyecto de servicio en la nube de Azure en Visual Studio.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y, en el menú contextual, seleccione **Publicar**.

**Si tiene un proyecto de aplicación web no habilitado para Azure:**

1. Cree o abra un proyecto de servicio en la nube de Azure en Visual Studio.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y, en el menú contextual, seleccione **Convertir** > **Convertir en proyecto de servicio en la nube de Azure**.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto de Azure que acaba de crear y, en el menú contextual, seleccione **Publicar**.

## <a name="sign-in-page"></a>Página de inicio de sesión

![Página de inicio de sesión](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Cuenta**: seleccione una cuenta o seleccione **Agregar una cuenta** en la lista desplegable de cuentas.

**Elija una suscripción**: elija la suscripción que desea usar para la implementación.

## <a name="settings-page---common-settings-tab"></a>Página Configuración: pestaña Configuración común

![Configuración común](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Servicio en la nube**: en la lista desplegable, seleccione un servicio en la nube existente o seleccione **&lt;Crear nuevo&gt;** y cree un servicio en la nube. El centro de datos aparece entre paréntesis para cada servicio en la nube. Se recomienda que la ubicación del centro de datos del servicio en la nube sea la misma ubicación del centro de datos de la cuenta de almacenamiento (Configuración avanzada).

**Entorno**: seleccione **Producción** o **Ensayo**. Elija el entorno de ensayo si desea implementar la aplicación en un entorno de prueba.

**Configuración de compilación**: seleccione **Depurar** o **Liberar**.

**Configuración de servicio**: seleccione **Nube** o **Local**.

**Habilitar Escritorio remoto para todos los roles**: seleccione esta opción si desea poder conectarse de forma remota al servicio. Esta opción se emplea principalmente para la solución de problemas. Para más información, vea [Habilitación de la conexión a Escritorio remoto para un rol de Azure Cloud Services mediante Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Habilitar Web Deploy para todos los roles web**: seleccione esta opción para habilitar la implementación web para el servicio. Debe seleccionar también la opción **Habilitar Escritorio remoto para todos los roles** para usar esta característica. Para obtener más información, vea [publicar un servicio en la nube con Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Página Configuración: pestaña Configuración avanzada

![Configuración avanzada](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Etiqueta de implementación**: acepte el nombre predeterminado o escriba un nombre de su elección. Para anexar la fecha a la etiqueta de implementación, deje activada la casilla.

**Cuenta de almacenamiento**: seleccione la cuenta de almacenamiento que desea usar para esta implementación, **&lt;Crear nuevo&gt; para crear una cuenta de almacenamiento. El centro de datos aparece entre paréntesis para cada cuenta de almacenamiento. Se recomienda que la ubicación del centro de datos de la cuenta de almacenamiento sea la misma ubicación del centro de datos del servicio en la nube (Configuración común).

La cuenta de almacenamiento de Azure almacena el paquete para la implementación de la aplicación. Una vez implementada la aplicación, el paquete se quita de la cuenta de almacenamiento.

**Eliminar implementación en caso de error**: seleccione esta opción para eliminar la implementación si se encuentra algún error durante la publicación. Desactive esta opción si desea mantener una dirección IP virtual para el servicio en la nube.

**Actualización de implementación**: seleccione esta opción si desea implementar solo los componentes actualizados. Este tipo de implementación puede ser más rápido que la implementación completa. Active esta opción si desea mantener una dirección IP virtual para el servicio en la nube.

**Actualización de implementación - configuración**: este cuadro de diálogo se usa para especificar con más detalle cómo desea actualizar los roles. Si elige **Actualización incremental**, cada instancia de la aplicación se actualizará una tras otra, para que la aplicación siempre esté disponible. Si elige **Actualización simultánea**, todas las instancias de la aplicación se actualizarán al mismo tiempo. La actualización simultánea es más rápida, pero es posible que el servicio no esté disponible durante el proceso de actualización.

![Configuración de implementación](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**Habilitar IntelliTrace**: especifique si desea habilitar IntelliTrace. Con IntelliTrace, puede registrar información de depuración amplia para una instancia de rol cuando se ejecuta en Azure. Si necesita encontrar la causa de un problema, puede utilizar los registros de IntelliTrace para recorrer su código desde Visual Studio como si se estuviera ejecutando en Azure. Para más información sobre IntelliTrace, consulte [Depuración de un servicio en la nube de Azure publicado con Visual Studio e IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Habilitar generación de perfiles**: especifique si desea habilitar la generación de perfiles de rendimiento. El generador de perfiles de Visual Studio le permite obtener un análisis exhaustivo de los aspectos de cálculo de cómo se ejecuta el servicio en la nube. Para más información sobre cómo usar el generador de perfiles de Visual Studio, consulte [Prueba del rendimiento de un servicio en la nube de Azure](./vs-azure-tools-performance-profiling-cloud-services.md).

**Habilitar Remote Debugger para todos los roles**: especifique si desea habilitar la depuración remota. Para más información sobre cómo depurar los servicios en la nube con Visual Studio, consulte [Depuración de una máquina virtual o un servicio en la nube de Azure en Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Página Configuración de Diagnósticos

![Configuración de diagnóstico](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Diagnósticos le permite solucionar los problemas de un servicio en la nube de Azure (o en una máquina virtual de Azure). Para más información sobre el diagnóstico, consulte [Configuración de Diagnósticos en Azure Cloud Services y Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Para más información sobre Application Insights, consulte [¿Qué es Application Insights?](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Página de resumen

![Página de resumen](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Perfil de destino**: puede optar por crear un perfil de publicación a partir de la configuración que eligió. Por ejemplo, puede crear un perfil para un entorno de pruebas y otro para producción. Para guardar este perfil, elija el icono **Guardar**. El asistente creará el perfil y lo guardará en el proyecto de Visual Studio. Para modificar el nombre del perfil, abra la lista **Perfil de destino** y, a continuación, elija **&lt;Administrar…&gt;**.

   > [!Note]
   > El perfil de publicación aparecerá en el Explorador de soluciones en Visual Studio y su configuración se escribirá en un archivo con la extensión .azurePubxml. La configuración se guarda como atributos de etiquetas XML.

## <a name="publishing-your-application"></a>Publicación de la aplicación

Una vez que ajuste toda la configuración de la implementación del proyecto, seleccione **Publicar** en la parte inferior del cuadro de diálogo. Puede supervisar el estado del proceso en la ventana **Resultados** de Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

- [Migración y publicación de una aplicación web en un servicio en la nube de Azure desde Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Información sobre cómo usar Visual Studio para publicar un servicio en la nube de Azure](./vs-azure-tools-publishing-a-cloud-service.md)

- [Depuración de un servicio en la nube de Azure publicado con Visual Studio e IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Prueba del rendimiento de un servicio en la nube de Azure](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Configuración de diagnósticos para Azure Cloud Services y virtual machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [¿Qué es Application Insights?](/azure/application-insights/app-insights-overview)