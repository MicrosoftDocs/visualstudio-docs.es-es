---
title: Implementar, publicar & actualizar paquetes de soluciones de SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8e55b01173e749395f60d189366a08907bdaccd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444975"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Implementar, publicar y actualizar paquetes de soluciones de SharePoint
  Después de desarrollar una solución de SharePoint en Visual Studio, puede implementar su archivo de paquete (.wsp) en un servidor de SharePoint local o publicarlo en un servidor de SharePoint remoto o local. Si implementa los archivos, puede personalizar cómo se implementan los archivos de paquete (.wsp).

> [!NOTE]
> Actualmente, solo se pueden publicar soluciones de espacio aislado en servidores remotos de SharePoint. Para obtener más información, consulte Consideraciones sobre [la solución](../sharepoint/sandboxed-solution-considerations.md)de espacio aislado .

## <a name="deploy-publish-and-upgrade"></a>Implementar, publicar y actualizar
 *La implementación* hace referencia a copiar un archivo de solución de SharePoint creado desde un proyecto de SharePoint en Visual Studio a un host local. En una solución implementada, puede configurar los pasos de implementación, como reciclar el grupo de Internet Information Services (IIS), activar la solución después de la implementación, etc. Para implementar, use el comando **Implementar** en el menú **Generar.** Para obtener más información, vea [Cómo: editar una configuración](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) de implementación de SharePoint y [Cómo: implementar y publicar una solución de SharePoint en un sitio de SharePoint local.](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)

 *La publicación* hace referencia a la carga de un archivo de solución de SharePoint de espacio aislado en un sitio remoto de SharePoint; es decir, un sitio ubicado en otro sistema. También puede publicar un archivo de solución de espacio aislado de SharePoint en un sitio de SharePoint local, pero independientemente de si el sitio publicado en es local o remoto, no puede configurar sus pasos de implementación.

 *La actualización* hace referencia a la actualización de una solución de SharePoint publicada de forma remota o local. Después de realizar cualquier cambio en la solución de SharePoint en Visual Studio, cambie el nombre del archivo de paquete de la solución, vuelva a publicar la solución y, a continuación, actualice la solución después de volver a publicarla correctamente. Si vuelve a publicar una solución publicada localmente, puede sobrescribir el archivo de solución existente.

## <a name="deploy-packages"></a>Implementar paquetes
 Puede implementar archivos de paquete en el servidor de SharePoint en el equipo de desarrollo para probar y depurar. También puede crear un archivo de paquete que puede instalar en otro equipo seleccionando el botón de opción **Publicar** en sistema de archivos en el cuadro de diálogo **Publicar.** El paquete se crea y se copia en la ruta de acceso del archivo local especificada. Para implementar una solución de SharePoint en el servidor local, use el comando **Implementar** en el menú **Compilar.** Para obtener más información, vea [Cómo: implementar y publicar una solución](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)de SharePoint en un sitio de SharePoint local.

 Para obtener información sobre cómo implementar una definición de lista, agregar un receptor de eventos y usar el Diseñador de características y el Diseñador de paquetes, vea [Tutorial: implementar una definición](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)de lista de tareas de proyecto .

## <a name="customize-the-deployment-process"></a>Personalizar el proceso de implementación
 En la tabla siguiente se muestran las dos configuraciones de implementación que puede usar al depurar e implementar una solución de SharePoint.

|Configuración de implementación|Descripción|
|------------------------------|-----------------|
|Valor predeterminado|La configuración de implementación predeterminada. Se realizan los siguientes pasos de implementación:<br /><br /> 1. Ejecute el comando pre-deployment.<br />2. Recicle el grupo de aplicaciones IIS.<br />3. Retirar la solución.<br />4. Agregue la solución.<br />5. Active las funciones.<br />6. Ejecute el comando post-deployment.<br /><br /> Cuando se desinstala un paquete, se realizan los siguientes pasos de retracción.<br /><br /> 1. Recicle el grupo de aplicaciones IIS.<br />2. Retirar la solución.|
|Sin activación|Esta configuración de implementación ejecuta los mismos pasos que la configuración predeterminada, pero omite el paso de activación.|

 Puede crear sus propias configuraciones de implementación para completar un solo paso o cambiar el orden de los pasos del proceso de implementación. Para obtener más información, vea [Cómo: editar una configuración](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)de implementación de SharePoint .

 También puede agregar comandos para ejecutarantes y después de la implementación. Para obtener más información, vea [Cómo: Establecer comandos](../sharepoint/how-to-set-sharepoint-deployment-commands.md)de implementación de SharePoint .

## <a name="publish-packages-to-a-remote-or-local-server"></a>Publicar paquetes en un servidor remoto o local
 Para publicar una solución de SharePoint de espacio aislado en un servidor remoto, en la barra de menús, elija **Compilar**, **Publicar**y, a continuación, en el cuadro de diálogo **Publicar,** elija el botón de opción Publicar en sitio de **SharePoint,** que proporciona la dirección URL del servidor remoto, como `https://someremoteserver.sharepoint.microsoftonline.com`.

 Para publicar una solución de SharePoint en un servidor local, en el cuadro de diálogo **Publicar,** elija el botón de opción Publicar en **sistema** de archivos, que proporciona una ruta de acceso del sistema local.

 Después de que una solución se publique correctamente en SharePoint, la solución aparece en la **Galería** de soluciones, donde puede activarla. Para obtener más información, vea [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto.](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)

### <a name="upgrade-published-packages"></a>Actualizar paquetes publicados
 Si realiza cambios en un proyecto de SharePoint en Visual Studio después de publicarlo, el paquete publicado debe actualizarse para incluir los cambios. Para actualizar correctamente, un paquete debe tener un nombre único. Si se encuentra un paquete con el mismo nombre en el sitio de SharePoint, que puede producirse al actualizar una aplicación existente, un error le alerta del conflicto de nombre de archivo y le permite cambiar el nombre del paquete. Después de volver a publicarse, el nuevo paquete aparece en el sitio de SharePoint y se puede actualizar. Un paquete actualizado actualiza la solución mediante el uso de datos del paquete anterior y, a continuación, activa la solución en SharePoint. Para obtener más información, vea [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto.](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)

## <a name="see-also"></a>Consulte también
- [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
