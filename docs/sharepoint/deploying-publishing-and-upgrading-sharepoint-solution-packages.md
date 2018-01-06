---
title: "Implementar, publicar y actualizar los paquetes de solución de SharePoint | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: 5efc1d99-2bd2-4f1a-a7b0-86c3b8f533f0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c1c8757de9b63c3fed75ec7e2ef7f61c89e18226
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-publishing-and-upgrading-sharepoint-solution-packages"></a>Implementar, publicar y actualizar paquetes de soluciones deSharePoint
  Después de desarrollar una solución de SharePoint en Visual Studio, puede implementar su archivo de paquete (.wsp) en un servidor de SharePoint local o publicarlo en un servidor de SharePoint local o remoto. Si implementa los archivos, puede personalizar cómo se implementan los archivos del paquete (.wsp).  
  
> [!NOTE]  
>  Actualmente, sólo las soluciones en espacio aislado se pueden publicar en servidores remotos de SharePoint. Para obtener más información, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="deploying-publishing-and-upgrading"></a>Implementar, publicar y actualizar  
 *Implementar* hace referencia a la copia de un archivo de solución de SharePoint creado a partir de un proyecto de SharePoint en Visual Studio en un host local. En una solución implementada, puede configurar los pasos de implementación, como el reciclaje del conjunto de servicios de Internet Information Server (IIS), la activación de la solución después de la implementación y así sucesivamente. Para implementar, usar el **implementar** comando el **generar** menú. Para obtener más información, consulte [Cómo: editar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) y [Cómo: implementar y publicar una solución de SharePoint en un sitio de SharePoint Local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *Publicar* hace referencia a cargar un archivo de solución en espacio aislado de SharePoint en SharePoint remoto sitio; es decir, un sitio ubicado en otro sistema. También puede publicar un archivo de solución en espacio aislado de SharePoint en un sitio de SharePoint local, pero independientemente de si el sitio que se publican en es local o remoto, no se puede configurar sus pasos de implementación.  
  
 *Actualizar* hace referencia a la actualización de una existente de forma remota o localmente publicado solución de SharePoint. Una vez realizados los cambios a la solución de SharePoint en Visual Studio, cambiar el nombre de archivo del paquete de la solución, volver a publicar la solución y, a continuación, actualice la solución después de correctamente vuelve a publicar. Si se vuelve a publicar una solución publicada localmente, puede sobrescribir el archivo de solución existente.  
  
## <a name="deploying-packages"></a>Implementación de paquetes  
 Puede implementar archivos de paquete en el servidor de SharePoint en el equipo de desarrollo para probar y depurar. También puede crear un archivo de paquete que puede instalar en otro equipo eligiendo el **publicar en el sistema de archivos** botón de opción en el **publicar** cuadro de diálogo. El paquete se crea y se copian en la ruta de acceso de archivo local especificado. Para implementar una solución de SharePoint en el servidor local, utilice la **implementar** comando el **generar** menú. Para obtener más información, consulte [Cómo: implementar y publicar una solución de SharePoint en un sitio de SharePoint Local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Para obtener información sobre cómo implementar una definición de lista, agregar un receptor de eventos y usar el Diseñador de características y el Diseñador de paquetes, consulte [Tutorial: implementar una definición de lista de tareas de proyecto](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## <a name="customizing-the-deployment-process"></a>Personalizar el proceso de implementación  
 La tabla siguiente muestran las dos configuraciones de implementación que puede usar al depurar e implementar una solución de SharePoint.  
  
|Configuración de implementación|Descripción|  
|------------------------------|-----------------|  
|Default|La configuración de implementación predeterminada. Se realizan los pasos de implementación siguientes:<br /><br /> 1.  Ejecute el comando anterior a la implementación.<br />2.  Reciclar el grupo de aplicaciones de IIS.<br />3.  Retirar la solución.<br />4.  Agregar la solución.<br />5.  Activar las características.<br />6.  Comando de ejecución posterior a la implementación.<br /><br /> Cuando se desinstala un paquete, se realizan los siguientes pasos de retracción.<br /><br /> 1.  Reciclar el grupo de aplicaciones de IIS.<br />2.  Retirar la solución.|  
|Sin activación|Esta configuración de implementación ejecuta los mismos pasos como la configuración predeterminada, pero omite el paso de activación.|  
  
 Puede crear sus propias configuraciones de implementación para completar un paso único o cambiar el orden de los pasos del proceso de implementación. Para obtener más información, consulte [Cómo: editar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
 También puede agregar comandos que se ejecutarán antes y después de la implementación. Para obtener más información, consulte [Cómo: establecer comandos de implementación de SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## <a name="publishing-packages-to-a-remote-or-local-server"></a>Publicar paquetes en un servidor remoto o Local  
 Para publicar una solución en espacio aislado de SharePoint en un servidor remoto, en la barra de menús, elija **generar**, **publicar**y, a continuación, en la **publicar** diálogo cuadro, elija la **Publicar en un sitio de SharePoint** botón de opción, proporcionar la dirección URL del servidor remoto, como **https://someremoteserver.sharepoint.microsoftonline.com**.  
  
 Para publicar una solución de SharePoint a un servidor local, en la **publicar** diálogo cuadro, elija la **publicar en el sistema de archivos** botón de opción, proporcionar una ruta de acceso de sistema local.  
  
 Después de una solución se publica correctamente en SharePoint, la solución aparece en el **Galería de soluciones** donde puede activarla. Para obtener más información, consulte [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### <a name="upgrading-published-packages"></a>Actualizar los paquetes publicados  
 Si realiza cambios en un proyecto de SharePoint en Visual Studio después de haberlo publicado, el paquete publicado debe actualizarse para incluir los cambios. Para actualizar correctamente, un paquete debe tener un nombre único. Si se encuentra un paquete con el mismo nombre en el sitio de SharePoint, que puede producirse durante la actualización de una aplicación existente: las alertas de un error al nombre de archivo están en conflicto y le permite cambiar el nombre del paquete. Después de que se publique de nuevo, el nuevo paquete aparece en el sitio de SharePoint y se puede actualizar. Un paquete actualizado actualiza la solución mediante el uso de datos del paquete anterior y, a continuación, activa la solución en SharePoint. Para obtener más información, consulte [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  