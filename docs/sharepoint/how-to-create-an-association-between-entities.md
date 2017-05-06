---
title: "C&#243;mo crear una asociaci&#243;n entre entidades"
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
  - "AssociationGroupTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [desarrollo de SharePoint en Visual Studio], asociar tipos de contenido externos"
  - "BDC [desarrollo de SharePoint en Visual Studio], asociaciones entre entidades"
  - "BDC [desarrollo de SharePoint en Visual Studio], crear una asociación"
  - "BDC [desarrollo de SharePoint en Visual Studio], relacionar entidades"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], asociar tipos de contenido externos"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], asociaciones entre entidades"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], crear una asociación"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], relacionar entidades"
ms.assetid: 0c095df8-1f40-4c4d-9fed-e125a8429724
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# C&#243;mo crear una asociaci&#243;n entre entidades
  Puede definir las relaciones entre las entidades del Modelo de conectividad a datos profesionales \(BDC\) creando asociaciones.  Visual Studio genera métodos que proporcionan a los consumidores del modelo información sobre cada asociación.  Estos métodos se pueden utilizar en elementos web de SharePoint, listas, o aplicaciones personalizadas de mostrar las relaciones de datos en una interfaz de usuario \(UI\).  
  
 Puede crear dos tipos de asociaciones en el diseñador de BDC: asociaciones basadas en clave externa y asociaciones sin clave externa.  Para obtener más información, vea [Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md).  
  
### Para crear una asociación entre entidades  
  
1.  En la pestaña de **BusinessDataConnectivity** de **Cuadro de herramientas**, elija el elemento de **Asociación** .  
  
2.  En el diseñador de BDC, elija la entidad de origen, y elija la entidad de destino.  
  
     Aparecerá el **Editor de asociaciones**.  
  
3.  Si desea crear una asociación basada en clave externa, active la casilla **Es una asociación de clave externa**.  
  
    1.  En la columna de **Id. de origen** de la tabla de **Asignación de identificadores** , elija el identificador situado junto a cada descriptor coincidente que aparece en la columna de **Campo** .  
  
         Por ejemplo, en la columna **Id. de origen**, seleccione `ContactID` situado junto al descriptor de tipos `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` y el descriptor de tipos `ReadItem.salesOrder.SalesOrder.ContactID`.  
  
4.  Si desea crear una asociación sin clave externa, desactive la casilla **Es una asociación de clave externa**.  
  
5.  Elija el botón **Aceptar**.  
  
6.  En el diseñador de BDC, aparece una línea que representa la asociación entre la entidad de origen y la de destino.  
  
     Visual Studio agrega un método de navegación mediante asociaciones a la clase de servicio de la entidad de destino y a la de la entidad de origen.  Para obtener más información sobre los métodos de navegación mediante asociaciones, vea. [Operaciones admitidas](http://go.microsoft.com/fwlink/?LinkId=169286)  
  
7.  En el método de navegación mediante asociaciones de la entidad de origen, agregue código que devuelva una colección de entidades de destino.  
  
8.  En el método de navegación mediante asociaciones de la entidad de destino, agregue código que devuelva la entidad de origen relacionada.  
  
     Para obtener ejemplos de métodos de navegación mediante asociaciones, vea [Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md).  
  
## Vea también  
 [Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Tutorial: Crear una lista externa en SharePoint con datos profesionales](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  