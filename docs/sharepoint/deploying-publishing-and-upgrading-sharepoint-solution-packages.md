---
title: Implementar, publicar y actualizar los paquetes de solución de SharePoint | Microsoft Docs
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8bef002d1d32abf4f97a63f284545cbaa6eee403
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853463"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Implementar, publicar y actualizar los paquetes de solución de SharePoint
  Después de desarrollar una solución de SharePoint en Visual Studio, puede implementar su archivo de paquete (.wsp) en un servidor de SharePoint local o publicarlo en un servidor de SharePoint remoto o local. Si implementa los archivos, puede personalizar cómo se implementan los archivos del paquete (.wsp).  
  
> [!NOTE]  
>  Actualmente, solo las soluciones en espacio aislado pueden publicarse en servidores remotos de SharePoint. Para obtener más información, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="deploy-publish-and-upgrade"></a>Implementar, publicar y actualizar
 *Implementar* se refiere a copiar un archivo de solución de SharePoint creado desde un proyecto de SharePoint en Visual Studio para un host local. En una solución implementada, puede configurar los pasos de implementación, como el reciclaje del grupo de Internet Information Services (IIS), la activación de la solución después de la implementación y así sucesivamente. Para implementar, usar el **implementar** comando el **compilar** menú. Para obtener más información, vea [Cómo: Editar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) y [Cómo: Implementar y publicar una solución de SharePoint en un sitio de SharePoint Local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *Publicación* hace referencia a cargar un archivo de solución en espacio aislado de SharePoint en SharePoint remoto sitio; es decir, un sitio ubicado en otro sistema. También puede publicar un archivo de solución en espacio aislado de SharePoint en un sitio de SharePoint local, pero independientemente de si el sitio publicado en es local o remoto, no se puede configurar sus pasos de implementación.  
  
 *Actualizar* hace referencia a la actualización de una solución de SharePoint publicado localmente o de existente de forma remota. Una vez realizados los cambios a la solución de SharePoint en Visual Studio, cambiar el nombre de archivo del paquete de la solución, vuelva a publicar la solución y, a continuación, actualice la solución después de correctamente vuelve a publicar. Si se vuelve a publicar una solución publicada localmente, puede sobrescribir el archivo de solución existente.  
  
## <a name="deploy-packages"></a>Implementar paquetes
 Puede implementar los archivos de paquete en el servidor de SharePoint en el equipo de desarrollo para probar y depurar. También puede crear un archivo de paquete que se puede instalar en otro equipo eligiendo el **publicar en el sistema de archivos** botón de opción en el **publicar** cuadro de diálogo. El paquete se creó y copió en la ruta de acceso de archivo local especificado. Para implementar una solución de SharePoint en el servidor local, utilice el **implementar** comando el **compilar** menú. Para obtener más información, vea [Cómo: Implementar y publicar una solución de SharePoint en un sitio de SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Para obtener información sobre cómo implementar una definición de lista, agregar un receptor de eventos y usar el Diseñador de características y el Diseñador de paquetes, consulte [Tutorial: Implementar una definición de lista de tareas de proyecto](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## <a name="customize-the-deployment-process"></a>Personalizar el proceso de implementación
 La siguiente tabla muestra las dos configuraciones de implementación que puede usar al depurar e implementar una solución de SharePoint.  
  
|Configuración de implementación|Descripción|  
|------------------------------|-----------------|  
|Default|La configuración de implementación de forma predeterminada. Se realizan los pasos de implementación siguientes:<br /><br /> 1.  Ejecute el comando anterior a la implementación.<br />2.  Recicle el grupo de aplicaciones de IIS.<br />3.  Retirar la solución.<br />4.  Agregue la solución.<br />5.  Activar las características.<br />6.  Ejecutar comando posterior a la implementación.<br /><br /> Cuando se desinstala un paquete, se realizan estos pasos.<br /><br /> 1.  Recicle el grupo de aplicaciones de IIS.<br />2.  Retirar la solución.|  
|Sin activación|Esta configuración de implementación ejecuta los mismos pasos como la configuración predeterminada, pero omite el paso de activación.|  
  
 Puede crear sus propias configuraciones de implementación para completar un paso único o cambiar el orden de los pasos del proceso de implementación. Para obtener más información, vea [Cómo: Editar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  

 También puede agregar comandos deben ejecutarse antes y después de la implementación. Para obtener más información, vea [Cómo: Establecer comandos de implementación de SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## <a name="publish-packages-to-a-remote-or-local-server"></a>Publicar paquetes en un servidor remoto o local
 Para publicar una solución en espacio aislado de SharePoint a un servidor remoto, en la barra de menús, elija **compilar**, **publicar**y, a continuación, en el **publicar** cuadro de diálogo, seleccione el **Publicar en el sitio de SharePoint** botón de opción, proporcionando la dirección URL del servidor remoto, como **https://someremoteserver.sharepoint.microsoftonline.com**.  
  
 Para publicar una solución de SharePoint a un servidor local, en el **publicar** diálogo cuadro, elija el **publicar en el sistema de archivos** botón de opción, que proporciona una ruta de acceso de sistema local.  
  
 Después de una solución se publica correctamente en SharePoint, la solución aparece en el **Galería de soluciones** donde puede activarla. Para obtener más información, vea [Cómo: Implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### <a name="upgrade-published-packages"></a>Actualizar los paquetes publicados
 Si realiza los cambios en un proyecto de SharePoint en Visual Studio después de haberlo publicado, el paquete publicado debe actualizarse para incluir los cambios. Para actualizar correctamente, un paquete debe tener un nombre único. Si se encuentra un paquete con el mismo nombre en el sitio de SharePoint, que puede producirse al actualizar una aplicación existente: las alertas de un error en el nombre de archivo entran en conflicto y le permite cambiar el nombre del paquete. Después de que vuelva a publicarse, el nuevo paquete aparece en el sitio de SharePoint y se puede actualizar. Un paquete actualizado actualiza la solución mediante el uso de datos desde el paquete anterior y, a continuación, activa la solución en SharePoint. Para obtener más información, vea [Cómo: Implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Vea también
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
