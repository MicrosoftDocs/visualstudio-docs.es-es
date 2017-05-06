---
title: "C&#243;mo: Agregar un par&#225;metro a un m&#233;todo"
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
  - "BDC [desarrollo de SharePoint en Visual Studio], agregar un método a un parámetro"
  - "BDC [desarrollo de SharePoint en Visual Studio], parámetros de métodos"
  - "BDC [desarrollo de SharePoint en Visual Studio], parámetro"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], agregar un método a un parámetro"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], parámetros de métodos"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], parámetro"
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# C&#243;mo: Agregar un par&#225;metro a un m&#233;todo
  Utilice un parámetro para pasar información al método o devolver información de un método.  Todos los métodos deben tener al menos un parámetro.  Para obtener más información sobre cómo diseñar un parámetro para admitir el tipo de método que desea crear, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Cuando agrega un parámetro al método, Visual Studio agrega el elemento `<Parameter>` al XML del archivo del modelo de su proyecto.  Para obtener más información sobre los atributos de un elemento de `<Parameter>` , vea [de navegación](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### Para agregar un parámetro a un método  
  
1.  Agregue un método a una entidad.  
  
2.  En la barra de menú, elija **Visualización**, **Otras ventanas**, **Detalles del método de BDC**.  
  
     Se abre la ventana **Detalles del método de BDC**.  Para obtener más información, vea [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  En la ventana **Detalles del método de BDC**, expanda el nodo del método y, a continuación, expanda **Parámetros**.  
  
4.  En la lista de **Agregar un parámetro** , elija **Crear parámetro**.  
  
     Bajo el nodo **Parámetros** aparece un nuevo parámetro.  
  
5.  En la barra de menús, elija **Ver** y después elija **Ventana Propiedades**.  
  
6.  En la ventana **Propiedades**, establezca la propiedad **Name** en cualquier nombre que tenga sentido.  Por ejemplo, si el método va a devolver clientes, podría denominar el método ObtenerClientes.  
  
7.  En la ventana de **Detalles del método de BDC** , abra la lista que aparece para la dirección del parámetro y, a continuación **En**, **InOut**, **Salida**, o **Volver**.  
  
     Para obtener más información sobre la dirección que elegir para el método de tipo que está creando, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Modifique el descriptor de tipos del parámetro.  Para obtener más información, vea [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## Vea también  
 [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  