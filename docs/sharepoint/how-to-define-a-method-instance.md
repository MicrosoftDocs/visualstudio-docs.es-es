---
title: "C&#243;mo: Definir la instancia de un m&#233;todo | Microsoft Docs"
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
  - "BDC [desarrollo de SharePoint en Visual Studio], método"
  - "BDC [desarrollo de SharePoint en Visual Studio], instancia de método"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], método"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], instancia de método"
ms.assetid: f0c8a686-c0de-414e-8de9-f228f59d1eb3
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: Definir la instancia de un m&#233;todo
  Debe definir por lo menos una instancia para cada método de su modelo.  
  
 Agregue una instancia de método utilizando la ventana **Detalles del método de BDC**.  Al agregar la instancia del método, Visual Studio agrega un elemento `<MethodInstance>` al XML del archivo del modelo de su proyecto.  Para obtener más información sobre los atributos de un elemento de `<MethodInstance>` , vea [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### Para definir una instancia de método  
  
1.  En la ventana **Detalles del método de BDC**, expanda el nodo de un método y, a continuación, expanda **Instancias**.  
  
2.  En la lista de **Agregar una instancia de método** , elija **Crear instancia de Finder**.  
  
     Una nueva instancia del método aparece bajo el nodo **Instancias**.  
  
3.  En la barra de menú, elija **Visualización**, elija **Ventana Propiedades**.  
  
4.  En la ventana **Propiedades**, establezca las propiedades de la instancia del método.  Para obtener más información sobre cada propiedad, vea [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## Vea también  
 [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  