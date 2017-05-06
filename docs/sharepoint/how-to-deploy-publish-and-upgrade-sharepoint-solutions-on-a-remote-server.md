---
title: "C&#243;mo: Implementar, publicar y actualizar una soluci&#243;n de SharePoint en un servidor remoto"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "implementar [desarrollo de SharePoint en Visual Studio]"
  - "implementación remota [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, implementar"
  - "desarrollo de SharePoint en Visual Studio, implementación remota"
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# C&#243;mo: Implementar, publicar y actualizar una soluci&#243;n de SharePoint en un servidor remoto
  Además de implementar las soluciones de SharePoint en el sistema local, puede publicar las soluciones en espacio aislado de SharePoint a los sitios remotos o sitios locales de SharePoint.  El proceso de publicación remoto copia el archivo .wsp en el servidor de SharePoint, instala la solución y, a continuación permite activar la solución.  También puede actualizar ninguna instalación remota de la solución de SharePoint después de que los cambios se realicen a él.  
  
## Para publicar una solución en espacio aislado de SharePoint en un servidor remoto de SharePoint  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el proyecto de SharePoint en espacio aislado que desea publicar y, a continuación **Publicar**.  
  
2.  En el cuadro de diálogo de **Publicar** , elija el botón de opción de **Publicar el sitio de SharePoint** , y después escriba una dirección URL para un sitio conectado de publicación, como en el ejemplo siguiente: https:\/\/mytestsite.sharepoint.microsoftonline.com.  
  
3.  Elija el botón de opción de **Abra la página desde la galería de soluciones en el explorador después de publicar** para ver la lista de soluciones en la página de **Galería de soluciones** después de publicar.  
  
4.  Elija el botón de **Publicar** .  
  
5.  Inicie sesión en el servidor remoto si se requiere la autenticación de usuario.  
  
     El progreso de la publicación aparece en la ventana de Visual Studio **salida** .  Cuando finaliza el proceso, el archivo de solución \(.wsp\) instalado en el servidor remoto de SharePoint.  Sin embargo, todavía debe producirse antes de que se puede utilizar en SharePoint.  
  
6.  En la página de **Galería de soluciones** , seleccione la aplicación de SharePoint y en la cinta de opciones, elija el botón de **Activación** .  
  
7.  En el cuadro de diálogo de **Active la solución** , en la cinta de opciones, elija el botón de **Activación** de nuevo.  
  
     La columna de **Estado** en la página de **Galería de soluciones** indica que la aplicación está activa.  
  
## Para actualizar una solución en espacio aislado de SharePoint en un servidor remoto de SharePoint  
 Si una solución en espacio aislado de SharePoint se publica ya en un servidor remoto, el proceso siguiente permite actualizarla después de realizar cambios en la aplicación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  Cambie el nombre del paquete de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Para ello, en **Explorador de soluciones** abre el paquete.  Aparece en **Explorador de paquetes**.  
  
2.  En **Explorador de paquetes**, en el cuadro de **Name** , cambie el nombre del paquete a un nombre único.  
  
3.  Guarde el proyecto.  
  
4.  En **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación **Publicar**.  
  
5.  En el cuadro de diálogo de **Publicar** , elija el botón de opción de **Publicar el sitio de SharePoint** y, a continuación, si falta la dirección URL del servidor remoto donde se guarda la solución, éntrelo en.  
  
6.  Elija el botón de opción de **Abra la página desde la galería de soluciones en el explorador después de publicar** para ver la lista de soluciones en la página de **Galería de soluciones** después de publicar.  
  
7.  Elija el botón de **Publicar** .  
  
8.  Inicie sesión en el servidor remoto si se requiere la autenticación de usuario.  
  
     Si inició sesión en el servidor remoto recientemente, la autenticación no puede ser necesaria.  
  
     Si la versión anterior de la aplicación que todavía tiene el mismo nombre existe en el servidor de SharePoint, recibirá un error que un paquete con el mismo nombre ya existe en el servidor de SharePoint.  Debe cambiar el nombre del paquete a un nombre único antes de publicar.  
  
9. Elija la nueva aplicación en SharePoint y, a continuación, en la cinta de opciones, elija el botón de **Actualizar** .  
  
10. En el cuadro de diálogo de **Actualice la solución** , en la cinta de opciones, elija el botón de **Actualizar** de nuevo.  La columna de **Estado** en la página de **Galería de soluciones** ahora debe indicar que la aplicación está activa.  
  
     La versión anterior de la solución está desactivada, la nueva versión de la solución se actualizan con los datos mantenidos de la solución anterior, y la nueva solución se provoca en SharePoint.  
  
## Vea también  
 [Cómo: Implementar y publicar una solución de SharePoint en un sitio de SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Crear paquetes de soluciones de SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Cómo: Personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Cómo: Agregar y quitar características y elementos de un paquete con el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  