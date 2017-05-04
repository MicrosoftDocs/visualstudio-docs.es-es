---
title: "Implementar, publicar y actualizar paquetes de soluciones de
SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SharePointProjectPropertyTab"
  - "VS.SharePointTools.Project.Publishing"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "implementar [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, implementar"
ms.assetid: 5efc1d99-2bd2-4f1a-a7b0-86c3b8f533f0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Implementar, publicar y actualizar paquetes de soluciones de
SharePoint
  Después de desarrollar una solución de SharePoint en Visual Studio, puede implementar el archivo empaquetado \(.wsp\) en un servidor de SharePoint local o publicarlo en un servidor remoto o local de SharePoint.  Si implementa los archivos, puede personalizar cómo se implementan los archivos empaquetados \(.wsp\).  
  
> [!NOTE]  
>  Actualmente, sólo las soluciones en espacio aislado se pueden publicar en los servidores remotos de SharePoint.  Para obtener más información, vea [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
## Implementación, publicación, y actualización  
 *La implementación* hace referencia a copiar un archivo de solución de SharePoint de compilación de un proyecto de SharePoint en Visual Studio a un host local.  En una solución implementada, puede configurar los pasos de implementación, como el reciclaje de conjunto de \(IIS\) de IIS, y generar la solución después de la implementación, y así sucesivamente.  Para implementar, utilice el comando de **Implementación** en el menú de **Compilación** .  Para obtener más información, vea [Cómo: Modificar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) y [Cómo: Implementar y publicar una solución de SharePoint en un sitio de SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *La publicación* hace referencia a cargar un archivo de solución en espacio aislado de SharePoint en un sitio de SharePoint remoto; es decir, un sitio ubicado en otro sistema.  También puede publicar un archivo de solución en espacio aislado de SharePoint en un sitio de SharePoint local, pero independientemente de si el sitio publicado es local o remoto, no puede configurar sus pasos de implementación.  
  
 *La actualización* hace referencia a actualizar una existente de la solución de forma remota o localmente publicada de SharePoint.  Después de que cualquier cambio que se realice en la solución de SharePoint en Visual Studio, cambia el nombre de archivo del paquete de la solución, publicar la solución y, a continuación actualiza la solución después de publicar correctamente.  Si vuelve a publicar una solución localmente publicada, puede sobrescribir el archivo de solución existente.  
  
## Implementar paquetes  
 Puede implementar los archivos de paquete en el servidor de SharePoint en el equipo de desarrollo para probar y depurar.  También puede crear un archivo empaquetado que puede instalar en otro equipo mediante el botón de opción de **Publicar en el sistema de archivos** en el cuadro de diálogo de **Publicar** .  El paquete se crea y se copia a la ruta de acceso local especificada.  Para implementar una solución de SharePoint en el servidor local, utilice el comando de **Implementación** en el menú de **Compilación** .  Para obtener más información, vea [Cómo: Implementar y publicar una solución de SharePoint en un sitio de SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Para obtener información sobre cómo implementar una definición de lista, agregar un receptor de eventos y usar el Diseñador de características y el Diseñador de paquetes, vea [Tutorial: Implementar una definición de lista de tareas de proyecto](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## Personalizar el proceso de implementación  
 En la tabla siguiente se muestran las dos configuraciones de implementación que puede utilizar para depurar e implementar una solución de SharePoint.  
  
|Configuración de implementación|Descripción|  
|-------------------------------------|-----------------|  
|Valor|Configuración de implementación predeterminada.  Se siguen estos pasos de implementación:<br /><br /> 1.  Comando de la pre\- implementación run.<br />2.  Recicla el grupo de aplicaciones de IIS.<br />3.  Contraer la solución.<br />4.  Agregue la solución.<br />5.  Activar las características.<br />6.  Ejecute el comando de la POST\- implementación.<br /><br /> Cuando se desinstala un paquete, se siguen estos pasos.<br /><br /> 1.  Recicla el grupo de aplicaciones de IIS.<br />2.  Contraer la solución.|  
|No hay activación|Esta configuración de implementación ejecuta los mismos pasos que la configuración predeterminada, pero omite el paso de activación.|  
  
 Puede crear configuraciones de implementación que se completen en un paso único o cambiar el orden de los pasos del proceso de implementación.  Para obtener más información, vea [Cómo: Modificar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
 También puede agregar comandos que se ejecuten antes y después de la implementación.  Para obtener más información, vea [Cómo: Establecer comandos de implementación de SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## Paquetes de publicación a un equipo remoto o en un servidor local  
 Para publicar una solución en espacio aislado de SharePoint en un servidor remoto, en la barra de menú, elija **Compilación**, **Publicar**y, a continuación, en el cuadro de diálogo de **Publicar** , elija el botón de opción de **Publicar el sitio de SharePoint** , proporcionando la dirección URL del servidor remoto, como https:\/\/someremoteserver.sharepoint.microsoftonline.com.  
  
 Para publicar una solución de SharePoint en un servidor local, en el cuadro de diálogo de **Publicar** , elija el botón de opción de **Publicar en el sistema de archivos** , proporcionando una ruta de acceso del sistema local.  
  
 Después de que una solución publique correctamente en SharePoint, la solución aparece en **Galería de soluciones** donde puede activarla.  Para obtener más información, vea [Cómo: Implementar, publicar y actualizar una solución de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### Actualizar los paquetes publicados  
 Si realiza cualquier cambio en un proyecto de SharePoint en Visual Studio una vez publicada, el paquete publicado debe actualizarse para incluir los cambios.  Para actualizar correctamente, un paquete debe tener un nombre único.  Si un paquete con el mismo nombre se encuentra en el sitio de SharePoint – que puede aparecer cuando se actualiza una aplicación existente – un error alerta en conflicto de nombre de archivo y permite cambiar el nombre del paquete.  Una vez republicada, el nuevo paquete en el sitio de SharePoint y se puede actualizar.  Un paquete actualizado actualiza la solución utilizando los datos del anterior paquete, y después genera la solución de SharePoint.  Para obtener más información, vea [Cómo: Implementar, publicar y actualizar una solución de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  