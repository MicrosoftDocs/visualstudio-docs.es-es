---
title: "Compilar y depurar soluciones de SharePoint"
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
  - "desarrollo de SharePoint en Visual Studio, compilar y depurar"
  - "desarrollo de SharePoint en Visual Studio, depurar"
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Compilar y depurar soluciones de SharePoint
  En líneas generales, la compilación y depuración de soluciones de SharePoint es similar a la compilación y depuración de otros tipos de proyectos en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Los temas de esta sección explican las diferencias que existen.  
  
## Salida del proyecto en soluciones de SharePoint  
 Al compilar las soluciones de SharePoint, se crean ensamblados y un archivo \(.wsp\) de paquete de solución.  En la tabla siguiente se muestran las ubicaciones de estos archivos durante una compilación.  
  
|Elemento de compilación|Carpeta de salida|  
|-----------------------------|-----------------------|  
|Ensamblado, base de datos de programa \(PDB\) y archivos .wsp.|\\bin\\debug de*ProjectName*o \\bin\\release de *ProjectName*|  
|Archivos de elementos de proyecto de SharePoint.|\\package\\debug de*ProjectName*o \\package\\release de *ProjectName*|  
|Archivos intermedios de compilación.|\\obj\\debug de*ProjectName*o \\obj\\release de *ProjectName*|  
|Archivos intermedios de empaquetado.|\\pkgobj\\debug de*ProjectName*o \\pkgobj\\release de *ProjectName*|  
  
## Compilar soluciones de SharePoint  
 Para compilar soluciones de SharePoint, el equipo de desarrollo debe tener instalada la versión correcta del servidor de SharePoint.  De lo contrario, la compilación de las soluciones de SharePoint sería igual que la compilación de otros tipos de proyectos en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Para obtener más información, vea [Cómo: Compilar soluciones de SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## Depurar y probar soluciones de SharePoint  
 Antes de realizar la depuración, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] copia el paquete .wsp en el servidor de SharePoint, activa el sitio y las características de ámbito web y, en ciertos casos, inicia el proyecto.  En otros casos, puede ser necesario abrir el proyecto manualmente.  Para obtener más información, vea [Solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) y [Depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## Depurar y comprobando las Soluciones de SharePoint mediante las características de ALM  
 Las características de Visual Studio Team System como prueba e IntelliTrace unit permiten más exactamente a los problemas de principio en soluciones de SharePoint.  La generación de perfiles permite buscar e identificar áreas problemáticas de rendimiento en las soluciones de SharePoint.  Para obtener más información, vea [Comprobar y depurar código de SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) y [Generar perfiles de rendimiento de aplicaciones de SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## Seguridad durante el proceso de compilación  
 Para poder empaquetar o implementar soluciones de SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debe tener los permisos necesarios para copiar los archivos en el servidor de SharePoint.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debe ejecutarse como un proceso elevado y la cuenta de usuario del servidor de SharePoint debe pertenecer al grupo Site Collection Administrators.  Además, debe especificar si el proyecto es una solución en espacio aislado o una solución de granja de servidores.  Para obtener más información, vea [Diferencias entre soluciones en espacio aislado y soluciones de granja](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## Utilizar el comando Limpiar  
 Cuando una solución de SharePoint se instala en un servidor de SharePoint para su depuración, el comando **Limpiar** no desinstala la solución.  En su lugar, las características deberás desactivarse a través de la configuración de SharePoint.  
  
## Vea también  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Examinar las conexiones de SharePoint utilizando el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  