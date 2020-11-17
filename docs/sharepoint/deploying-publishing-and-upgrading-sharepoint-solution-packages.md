---
title: Implementar, publicar, & actualizar paquetes de soluciones de SharePoint
description: Implementar, publicar y actualizar paquetes de soluciones de SharePoint. Personalizar el proceso de implementación. Publicar paquetes en un servidor remoto o local.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: ab97efc82575c31c8e05b73063c2b53a09691d2d
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672670"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Implementar, publicar y actualizar paquetes de soluciones de SharePoint
  Después de desarrollar una solución de SharePoint en Visual Studio, puede implementar su archivo de paquete (. wsp) en un servidor de SharePoint local o publicarlo en un servidor de SharePoint remoto o local. Si implementa los archivos, puede personalizar cómo se implementan los archivos de paquete (. wsp).

> [!NOTE]
> Actualmente, solo las soluciones en espacio aislado se pueden publicar en servidores de SharePoint remotos. Para obtener más información, vea [consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Implementar, publicar y actualizar
 La *implementación* de hace referencia a la copia de un archivo de solución de SharePoint generado a partir de un proyecto de SharePoint en Visual Studio en un host local. En una solución implementada, puede configurar los pasos de implementación, como el reciclaje del grupo de Internet Information Services (IIS), la activación de la solución después de la implementación, etc. Para implementar, use el comando **implementar** en el menú **compilar** . Para obtener más información, vea [Cómo: modificar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) y [Cómo: implementar y publicar una solución de SharePoint en un sitio de SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 La *publicación* hace referencia a la carga de un archivo de solución en espacio aislado de SharePoint en un sitio remoto de SharePoint; es decir, un sitio ubicado en otro sistema. También puede publicar un archivo de solución en espacio aislado de SharePoint en un sitio de SharePoint local, pero independientemente de si el sitio publicado en es local o remoto, no puede configurar sus pasos de implementación.

 La *actualización* hace referencia a la actualización de una solución existente de SharePoint publicada de forma local o remota. Una vez realizados los cambios en la solución de SharePoint en Visual Studio, cambie el nombre del archivo de paquete de la solución, vuelva a publicar la solución y, a continuación, actualice la solución después de que se haya republicado correctamente. Si vuelve a publicar una solución publicada localmente, puede sobrescribir el archivo de solución existente.

## <a name="deploy-packages"></a>Implementar paquetes
 Puede implementar archivos de paquete en el servidor de SharePoint en el equipo de desarrollo para probar y depurar. También puede crear un archivo de paquete que puede instalar en otro equipo eligiendo el botón de opción **publicar en el sistema de archivos** del cuadro de diálogo **publicar** . El paquete se crea y se copia en la ruta de acceso del archivo local especificada. Para implementar una solución de SharePoint en el servidor local, use el comando **implementar** en el menú **compilar** . Para obtener más información, vea [Cómo: implementar y publicar una solución de SharePoint en un sitio de SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Para obtener información sobre cómo implementar una definición de lista, agregar un receptor de eventos y usar el diseñador de características y el diseñador de paquetes, vea [Tutorial: implementar una definición de lista de tareas de proyecto](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Personalizar el proceso de implementación
 En la tabla siguiente se muestran las dos configuraciones de implementación que puede usar al depurar e implementar una solución de SharePoint.

|Configuración de la implementación|Descripción|
|------------------------------|-----------------|
|Default|La configuración de implementación predeterminada. Se llevan a cabo los siguientes pasos de implementación:<br /><br /> 1. Ejecute el comando anterior a la implementación.<br />2. reciclar el grupo de aplicaciones de IIS.<br />3. retirar la solución.<br />4. Agregar solución.<br />5. activar las características de.<br />6. ejecutar el comando posterior a la implementación.<br /><br /> Cuando se desinstala un paquete, se llevan a cabo los siguientes pasos de retracción.<br /><br /> 1. recicle el grupo de aplicaciones de IIS.<br />2. retirar la solución.|
|Sin activación|Esta configuración de implementación ejecuta los mismos pasos que la configuración predeterminada, pero omite el paso de activación.|

 Puede crear sus propias configuraciones de implementación para completar un solo paso o cambiar el orden de los pasos en el proceso de implementación. Para obtener más información, vea [Cómo: para editar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 También puede Agregar comandos para que se ejecuten antes y después de la implementación. Para obtener más información, vea [Cómo: establecer comandos de implementación de SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Publicar paquetes en un servidor remoto o local
 Para publicar una solución de SharePoint en espacio aislado en un servidor remoto, en la barra de menús, elija **compilar**, **publicar** y, a continuación, en el cuadro de diálogo **publicar** , elija el botón de opción **publicar en el sitio de SharePoint** y proporcione la dirección URL del servidor remoto, como `https://someremoteserver.sharepoint.microsoftonline.com` .

 Para publicar una solución de SharePoint en un servidor local, en el cuadro de diálogo **publicar** , elija el botón de opción **publicar en el sistema de archivos** y proporcione una ruta de acceso del sistema local.

 Una vez que una solución se publica correctamente en SharePoint, la solución aparece en la **Galería de soluciones** , donde puede activarla. Para obtener más información, vea [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Actualizar paquetes publicados
 Si realiza cambios en un proyecto de SharePoint en Visual Studio una vez publicado, el paquete publicado debe actualizarse para incluir los cambios. Para actualizar correctamente, un paquete debe tener un nombre único. Si se encuentra un paquete con el mismo nombre en el sitio de SharePoint, lo que puede producirse al actualizar una aplicación existente, un error le avisará del conflicto de nombres de archivo y le permitirá cambiar el nombre del paquete. Una vez que se ha vuelto a publicar, el nuevo paquete aparece en el sitio de SharePoint y se puede actualizar. Un paquete actualizado actualiza la solución mediante el uso de datos del paquete anterior y, a continuación, activa la solución en SharePoint. Para obtener más información, vea [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Consulte también
- [Empaquetado e implementación de soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
