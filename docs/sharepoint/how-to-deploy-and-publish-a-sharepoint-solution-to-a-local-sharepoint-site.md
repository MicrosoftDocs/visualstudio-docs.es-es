---
title: "C&#243;mo: Implementar y publicar una soluci&#243;n de SharePoint en un sitio de SharePoint local"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "implementar [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, implementar"
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# C&#243;mo: Implementar y publicar una soluci&#243;n de SharePoint en un sitio de SharePoint local
  Puede implementar o publicar las soluciones de SharePoint en un servidor de SharePoint local en el equipo de desarrollo.  El proceso de implementación copia el archivo .wsp en el servidor de SharePoint, instala la solución y, a continuación activa las características.  El proceso de publicación sólo copia el archivo .wsp en el servidor de SharePoint y lo instala.  Debe tratarlo manualmente para habilitarla en SharePoint.  
  
## Para implementar una solución de SharePoint en el servidor de SharePoint local  
  
1.  En **Explorador de soluciones**, elija el proyecto que desea implementar.  
  
2.  En la barra de menú, elija **Compilación**, **Implementar solución**.  
  
     El archivo .wsp se crea e instala en el servidor de SharePoint local.  Además, se activan las características.  
  
## Para publicar una solución de SharePoint en un servidor de SharePoint local  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el proyecto de SharePoint que desea publicar y elegir **Publicar**.  
  
2.  En el cuadro de diálogo de **Publicar** , elija el botón de opción de **Publicar en el sistema de archivos** .  
  
3.  En el cuadro de texto de **Ubicación de destino** , escriba una ruta de acceso local, y elija el botón de **Publicar** .  
  
     El progreso de la publicación aparece en la ventana de Visual Studio **salida** .  Cuando finaliza el proceso, el archivo de solución \(.wsp\) se instala en el servidor de SharePoint local.  Sin embargo, todavía debe activarse para utilizar en SharePoint.  Si existe el archivo de solución ya, se produce un error de y pregunta si desea sobrescribir el archivo existente.  Para obtener información sobre cómo actualizar el paquete, vea la sección en los paquetes remotos de actualización en [Cómo: Implementar, publicar y actualizar una solución de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## Vea también  
 [Cómo: Implementar, publicar y actualizar una solución de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Crear paquetes de soluciones de SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Cómo: Personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Cómo: Agregar y quitar características y elementos de un paquete con el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  