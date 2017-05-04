---
title: "Pautas para importar flujos de trabajo reutilizables | Microsoft Docs"
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
  - "importar elementos [desarrollo de SharePoint en Visual Studio]"
  - "flujos de trabajo reutilizables [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, importar elementos"
  - "desarrollo de SharePoint en Visual Studio, flujos de trabajo reutilizables"
ms.assetid: 851043dd-ecbe-49ab-b5b7-5ea7b699df12
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Pautas para importar flujos de trabajo reutilizables
  Para importar flujos de trabajo reutilizables creados en SharePoint Designer, use la plantilla de proyecto de flujo de trabajo reutilizable de SharePoint 2010 de importación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Esta plantilla importa un *flujo de trabajo* *declarativo* \(solo para [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\) y lo convierte en un *flujo de trabajo de código*, que es un flujo de trabajo que puede mejorarse con código de [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)].  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Sin embargo, la plantilla de flujo de trabajo reutilizable de SharePoint 2010 de importación solo puede importar soluciones de granja.  Si desea implementar el flujo de trabajo como una solución en espacio aislado, importela con la plantilla de paquete de solución de SharePoint 2010 de importación.  Sin embargo, de esta manera, no puede convertirlo en un flujo de trabajo de código y no podrá modificarlo como tal.  
  
## Importar flujos de trabajo reutilizables con la plantilla Importar flujo de trabajo reutilizable  
 Si importa un flujo de trabajo reutilizable utilizando la plantilla de flujo de trabajo reutilizable de SharePoint 2010 de importación, puede ejecutar o cambiar la solución como cualquier otra solución de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint, pero puede que tenga que corregir manualmente algunos elementos.  
  
### Importar formularios de tareas  
 La plantilla de proyecto de flujo de trabajo reutilizable de SharePoint 2010 de importación importa todos los formularios de asociación e iniciación, pero solo importa un formulario de tareas porque el esquema de flujo de trabajo de código sólo permite un formulario de tareas.  Cualquier formulario de tareas adicional procedente de la solución de flujo de trabajo original se sitúa en la carpeta **Otros archivos importados** del **Explorador de soluciones**.  
  
## Importar flujos de trabajo reutilizables con la plantilla de paquete de solución de SharePoint 2010 de importación  
 Si importa un flujo de trabajo reutilizable utilizando la plantilla de paquete de solución de SharePoint 2010 de importación, debe tener en cuenta los siguientes aspectos:  
  
-   Después de importar el flujo de trabajo, puede pasar a implementarlo y ejecutar en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eligiendo la tecla F5.  Sin embargo, si cambia algo en el flujo de trabajo de la solución importada, es posible que tenga que corregir manualmente los elementos del proyecto antes de poder implementar y ejecutar el flujo de trabajo.  
  
-   Dado que el flujo de trabajo es declarativo, no se puede agregar código.  Para convertir el flujo de trabajo en un flujo de trabajo de código, debe importarlo en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mediante la plantilla de flujo de trabajo reutilizable de SharePoint 2010 de importación.  
  
-   Aunque puede modificar el archivo del Diseñador de flujo de trabajo \(.xoml\) en la Vista de diseño, le recomendamos que lo modifique en la vista Código fuente, ya que el Diseñador de flujo de trabajo muestra falsos positivos.  
  
-   La depuración del flujo de trabajo no funciona con contenido declarativo.  No se alcanzan los puntos de interrupción especificados en [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)].  
  
## Importar soluciones de flujo de trabajo reutilizables globalmente  
 Los flujos de trabajo reutilizables globalmente no se pueden importar utilizando la plantilla de flujo de trabajo reutilizable de SharePoint 2010 de importación.  Para importar un flujo de trabajo reutilizable globalmente, tiene que convertirlo en un flujo de trabajo reutilizable que \- global o tiene que usar la plantilla de paquete de solución de SharePoint 2010 de importación.  
  
 Para convertir el flujo de trabajo, realice una copia del flujo de trabajo reutilizable globalmente en SharePoint Designer \(abriendo el menú contextual para el flujo de trabajo y elige **Guardar como copia**\).  A continuación importe el nuevo flujo de trabajo reutilizable con la plantilla de flujo de trabajo reutilizable de SharePoint 2010 de importación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Para importar el flujo de trabajo reutilizable globalmente sin modificar el, use la plantilla de paquete de solución de SharePoint 2010 de importación.  Si utiliza este método, el flujo de trabajo no se convierte en un flujo de trabajo de código y sigue siendo un flujo de trabajo declarativo.  
  
## Vea también  
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  