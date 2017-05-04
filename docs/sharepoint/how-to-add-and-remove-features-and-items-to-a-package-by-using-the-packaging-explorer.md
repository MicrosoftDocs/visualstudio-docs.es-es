---
title: "C&#243;mo: Agregar y quitar caracter&#237;sticas y elementos de un paquete con el explorador de empaquetado | Microsoft Docs"
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
  - "VS.SharePointTools.RAD.PackagingExplorer"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, paquetes"
ms.assetid: 549d5848-f0c9-42c6-b7f5-bc1e626a30e6
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# C&#243;mo: Agregar y quitar caracter&#237;sticas y elementos de un paquete con el explorador de empaquetado
  Para configurar un paquete para implementar elementos y características de SharePoint, puede utilizar el Explorador de empaquetado.  Puede ajustar los elementos y las características del proyecto de SharePoint dentro de su archivo .wsp.  
  
 También puede utilizar el Diseñador de paquetes para ver y volver a ordenar las características y cambiar el orden de activación.  Para obtener más información, vea [Cómo: Agregar y quitar características y elementos de un paquete con el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## Abrir el Explorador de empaquetado  
 Puede utilizar el procedimiento siguiente para abrir el Explorador de empaquetado, si su solución Visual Studio tiene un proyecto de SharePoint por lo menos.  El Explorador de empaquetado se abre automáticamente al ver una característica o diseñador de paquetes.  Después de cerrar todos los diseñadores y características de los paquetes, también se cierra el Explorador de empaquetado.  
  
#### Para abrir el Explorador de empaquetado  
  
1.  En la barra de menú, elija **Visualización**, **Otras ventanas**, **Explorador de empaquetado**.  
  
     **Explorador de empaquetado** Aparece en **Cuadro de herramientas**.  
  
## Agregar una característica a un paquete  
 Puede agregar características nuevas y existentes a un paquete utilizando el Explorador de empaquetado.  
  
#### Para agregar una característica de SharePoint  
  
1.  Abra **Explorador de empaquetado**, abra el menú contextual del proyecto y, a continuación **Agregue la característica**.  
  
#### Para mover una característica de SharePoint existente  
  
1.  Abra **Explorador de empaquetado**, y realice uno de los pasos siguientes:  
  
    -   Arrastre **Característica** en un proyecto a otro proyecto.  
  
    -   Abrir el menú contextual de una característica, elija **Cortado**, abra el menú contextual del proyecto al que desea mover la característica y, a continuación **Pegar**.  
  
    > [!NOTE]  
    >  Utilice este procedimiento si tiene más de un proyecto de SharePoint en la solución.  
  
## Validar una característica o un paquete  
 Puede identificar los posibles problemas de las características y los paquetes de SharePoint validando los archivos.  Las advertencias y los errores se muestran en la Ventana de salida y en la ventana Lista de errores.  
  
#### Para validar una característica o un paquete de SharePoint  
  
1.  Abra el **Explorador de empaquetado**.  
  
2.  Abra un menú contextual para una característica o paquete y, a continuación **validar**.  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  