---
title: Usar Cloud Services (soporte extendido)
description: Aprenda a crear e implementar un Cloud Services (soporte extendido) mediante Azure Resource Manager con Visual Studio
author: ghogen
manager: jmartens
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 01/25/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 289bc88d9aef40fdc260ce84395b1c4b9237c689
ms.sourcegitcommit: 2a50f4c1705baeee5c05580f04e3f468550f44e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2021
ms.locfileid: "106381611"
---
# <a name="create-and-deploy-to-cloud-services-extended-support-in-visual-studio"></a>Crear e implementar en Cloud Services (soporte extendido) en Visual Studio

A partir de la [versión 16,9 de Visual Studio 2019](https://visualstudio.microsoft.com/vs/), puede trabajar con los servicios en la nube mediante Azure Resource Manager, lo que simplifica considerablemente y moderniza el mantenimiento y la administración de los recursos de Azure. Esto lo habilita un nuevo servicio de Azure denominado *Cloud Services (soporte extendido)*. Puede publicar un servicio en la nube existente en Cloud Services (soporte extendido). Para obtener información sobre este servicio de Azure, consulte la [documentación de Cloud Services (soporte extendido)](/azure/cloud-services-extended-support/overview).

## <a name="publish-to-cloud-services-extended-support"></a>Publicar en Cloud Services (soporte extendido)

Al publicar el proyecto de servicio en la nube de Azure existente en Cloud Services (soporte extendido), se conserva la capacidad de publicar en un servicio en la nube de Azure clásico. En la versión 16,9 de Visual Studio 2019 y versiones posteriores, los proyectos de servicio en la nube clásica tienen una versión especial del comando **publicar** , **publicar (soporte extendido)**. Este comando aparece en el menú contextual de **Explorador de soluciones**.

Hay algunas diferencias al publicar en Cloud Services (soporte extendido). Por ejemplo, no se le pregunta si está publicando en **ensayo** o **producción**, ya que estas ranuras de implementación no forman parte del modelo de publicación de soporte extendido. En su lugar, con Cloud Services (compatibilidad ampliada), puede configurar varias implementaciones y cambiar las implementaciones en el Azure Portal. Aunque las herramientas de Visual Studio permiten establecer esto en 16,9, la característica de intercambio no se habilitará hasta una versión posterior de Cloud Services (compatibilidad ampliada) y puede producir un error en el momento de la implementación durante la versión preliminar.

Antes de publicar un servicio en la nube de Azure clásico en Cloud Services (soporte extendido), compruebe las cuentas de almacenamiento que usa el proyecto y asegúrese de que son cuentas de almacenamiento V1 o de almacenamiento V2. Los tipos de cuenta de almacenamiento clásico producirán un mensaje de error en el momento de la implementación. Asegúrese de comprobar la cuenta de almacenamiento usada por los diagnósticos. Para comprobar la cuenta de almacenamiento de diagnósticos, consulte [configuración de diagnósticos para Azure Cloud Services y máquinas virtuales](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Si el servicio usa una cuenta de almacenamiento clásica, puede actualizarla. vea [actualizar a una cuenta de almacenamiento de uso general V2](/azure/storage/common/storage-account-upgrade?tabs=azure-portal).  Para obtener información general sobre los tipos de cuentas de almacenamiento, consulte [información general](/azure/storage/common/storage-account-overview)de la cuenta de almacenamiento.

### <a name="to-publish-a-classic-azure-cloud-service-project-to-cloud-services-extended-support"></a>Para publicar un proyecto de servicio en la nube de Azure clásico en Cloud Services (soporte extendido)

1. Haga clic con el botón derecho en el nodo del proyecto en el proyecto de servicio en la nube de Azure (clásico) y elija **publicar (soporte extendido)..**.. Se abre el **Asistente para publicación** en la primera pantalla.

   ![Elija publicar (soporte extendido) en el menú.](./media/cloud-services-extended-support/publish-commands-on-menu.png)

   Aparece el Asistente para **publicación** .

   ![Página de inicio de sesión](./media/cloud-services-extended-support/publish-step1.png)

1. **Cuenta**: seleccione una cuenta o seleccione **Agregar una cuenta** en la lista desplegable de cuentas.

1. **Elija una suscripción**: elija la suscripción que desea usar para la implementación.

1. Elija **Siguiente** para ir a la página **Configuración**.

   ![Configuración común](./media/cloud-services-extended-support/publish-settings.png)

1. **Servicio en la nube (soporte extendido)** : mediante la lista desplegable, seleccione un servicio en la nube existente (soporte extendido) o seleccione **crear nuevo** y cree uno. El centro de datos se muestra entre paréntesis para cada servicio en la nube (soporte extendido). Se recomienda que la ubicación del centro de datos para el servicio en la nube (compatibilidad ampliada) sea la misma que la ubicación del centro de datos de la cuenta de almacenamiento.

   Si decide crear un nuevo servicio, verá el cuadro de diálogo **crear servicio en la nube (soporte extendido)** . Especifique la ubicación y el grupo de recursos que desea usar para el servicio en la nube (soporte extendido).

   ![Crear un servicio en la nube (soporte extendido)](./media/cloud-services-extended-support/extended-support-dialog.png)

1. **Configuración de compilación**: seleccione **Depurar** o **Liberar**.

1. **Configuración de servicio**: seleccione **Nube** o **Local**.

1. **Cuenta de almacenamiento**: seleccione la cuenta de almacenamiento que desea usar para esta implementación o **Crear nuevo** para crear una nueva. La región aparece entre paréntesis para cada cuenta de almacenamiento. Se recomienda que la ubicación del centro de datos de la cuenta de almacenamiento sea la misma ubicación del centro de datos del servicio en la nube (Configuración común).

   La cuenta de almacenamiento de Azure almacena el paquete para la implementación de la aplicación.

1. **Almacén de claves** : especifique el almacén de claves que contiene los secretos para este servicio en la nube (soporte extendido). Esta opción está habilitada si el escritorio remoto está habilitado o si los certificados se agregan a la configuración.

1. **Habilitar Escritorio remoto para todos los roles**: seleccione esta opción si desea poder conectarse de forma remota al servicio. Se le pedirá que especifique las credenciales.

   ![Configuración de escritorio remoto](./media/cloud-services-extended-support/remote-desktop-configuration.png)

1. Elija **Siguiente** para ir a la página **Configuración de diagnóstico**.

   ![Configuración de diagnóstico](./media/cloud-services-extended-support/diagnostics-settings.png)

   Diagnósticos le permite solucionar problemas de un servicio en la nube de Azure (soporte extendido). Para más información sobre el diagnóstico, consulte [Configuración de Diagnósticos en Azure Cloud Services y Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Para más información sobre Application Insights, consulte [¿Qué es Application Insights?](/azure/application-insights/app-insights-overview).

1. Haga clic en **Siguiente** para avanzar a la página de **resumen**.

   ![Resumen](./media/cloud-services-extended-support/publish-summary.png)

1. **Perfil de destino**: puede optar por crear un perfil de publicación a partir de la configuración que eligió. Por ejemplo, puede crear un perfil para un entorno de pruebas y otro para producción. Para guardar este perfil, elija el icono **Guardar**. El asistente creará el perfil y lo guardará en el proyecto de Visual Studio. Para modificar el nombre del perfil, abra la lista **Perfil de destino** y, a continuación, elija **Administrar…**.

   > [!Note]
   > El perfil de publicación aparece en Explorador de soluciones en Visual Studio y la configuración del perfil se escribe en un archivo con la extensión *. azurePubxml* . La configuración se guarda como atributos de etiquetas XML.

1. Una vez que ajuste toda la configuración de la implementación del proyecto, seleccione **Publicar** en la parte inferior del cuadro de diálogo. Puede supervisar el estado del proceso en la ventana de salida **Registro de actividad de Azure** de Visual Studio. Elija el vínculo **abrir en el portal** para 

¡Enhorabuena! Ha publicado el proyecto de servicio en la nube (soporte extendido) en Azure. Para volver a publicar con la misma configuración, puede volver a usar el perfil de publicación o repetir estos pasos para crear uno nuevo. La plantilla de Azure Resource Manager (ARM) y los parámetros que se usan para la implementación se guardan en la carpeta *bin/ \<configuration\> /Publish* .

## <a name="clean-up-azure-resources"></a>Limpieza de los recursos de Azure

Para limpiar los recursos de Azure que creó siguiendo este tutorial, vaya al [Azure portal](https://portal.azure.com), elija grupos de **recursos**, busque y abra el grupo de recursos que usó para crear el servicio en la nube (soporte extendido) y elija **Eliminar grupo de recursos**.

## <a name="next-steps"></a>Pasos siguientes

Configure la integración continua (CI) mediante el botón **Configurar** de la pantalla **Publicar**. Para más información, consulte la [documentación de Azure Pipelines](/azure/devops/pipelines/?view=azure-devops&preserve-view=true).
