---
title: "C&#243;mo: Agregar un archivo de recursos | Microsoft Docs"
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
  - "archivos de recursos [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, archivos de recursos"
ms.assetid: 2b4ac232-992e-4070-8e98-6f11eb88e1a8
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# C&#243;mo: Agregar un archivo de recursos
  Los comandos para agregar archivos de recursos se encuentran en el menú contextual del nodo de solución y de los nodos Característica en el Explorador de soluciones.  Para obtener más información, vea [Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
### Para agregar un archivo de recursos global a una solución de SharePoint  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra una solución de SharePoint.  
  
2.  En **Explorador de soluciones**, elija un nodo de proyecto de SharePoint y, a continuación, en la barra de menús, elija **Project**, **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo de **Agregar nuevo elemento** , elija la plantilla de **Archivo de recursos globales** , y elija el botón de **Add** .  
  
    > [!NOTE]  
    >  La plantilla de elemento de proyecto Archivo de recursos globales solo aparece cuando está seleccionado un elemento de proyecto de SharePoint.  
  
4.  En el cuadro de diálogo de **Agregar recurso** , elija una referencia cultural para el archivo de recursos, como inglés \(Estados Unidos\).  
  
     Este paso agrega un archivo de recursos global a la solución en el formato, resx de*x***.***culture***.**de recursos, por ejemplo, recurso1.en\-us.resx.  
  
5.  Cuando **Recursos \- Editor** se abre en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], agregue los recursos al archivo de recursos.  
  
### Para agregar un archivo de recursos de características a una característica de SharePoint  
  
1.  Si la solución de SharePoint no está abierto en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra la solución.  
  
2.  En **Explorador de soluciones**, abra el menú contextual para el nodo de **Características** y, a continuación **Agregue el recurso de características**.  
  
     Este paso agrega un archivo de recursos a la característica en el formato, resx de *ResourceFileName***.***culture***.**, por ejemplo, Feature1.en\-US.resx.  
  
3.  Cuando **Recursos \- Editor** se abre en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], agregue los recursos al archivo de recursos.  
  
## Vea también  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  