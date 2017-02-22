---
title: "C&#243;mo: Especificar d&#243;nde Visual Studio copia los archivos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "propiedad de ubicación de publicación"
  - "publicar, especificar ubicación"
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Especificar d&#243;nde Visual Studio copia los archivos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al publicar una aplicación mediante ClickOnce, la propiedad `Publish Location` especifica la ubicación donde se colocan los archivos de la aplicación y el manifiesto.  La ubicación puede ser una ruta de acceso de archivo o la ruta de acceso a un servidor FTP.  
  
 La propiedad `Publish Location` se puede especificar en la página **Publicar** del **Diseñador de proyectos** o mediante el Asistente para publicación.  Para obtener más información, consulte [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Cuando se instala más de una versión de una aplicación con ClickOnce, la instalación mueve las versiones anteriores de la aplicación a una carpeta llamada Archivo, en la ubicación de publicación que especifiques.  Al archivar las versiones anteriores de esta manera, el directorio de instalación se mantiene limpio de carpetas de versiones anteriores.  
  
### Para especificar una ubicación de publicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto**, haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Publicar**.  
  
3.  En el campo **Ubicación de publicación**, escriba la ubicación de publicación mediante uno de los siguientes formatos:  
  
    -   Para publicar en un recurso compartido de archivos o en una ruta de acceso de disco, escriba la ruta mediante una ruta de acceso UNC \(\\\\Server\\NombreAplicación\) o una ruta de acceso de archivo \(C:\\Deploy\\NombreAplicación\).  
  
    -   Para publicar en un servidor FTP, escriba la ruta de acceso con el formato ftp:\/\/ftp.microsoft.com\/NombreAplicación.  
  
     Tenga en cuenta que debe haber texto en el cuadro **Ubicación de publicación** para que el botón Examinar \(**...**\) funcione.  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)