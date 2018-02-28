---
title: "Cómo: crear una asociación entre entidades | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 49b4d68a8d957462954c998d96e9309944cdb9f5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-an-association-between-entities"></a>Cómo crear una asociación entre entidades
  Puede definir las relaciones entre entidades en el modelo de conectividad de datos profesionales (BDC) mediante la creación de asociaciones. Visual Studio genera los métodos que proporcionan los consumidores del modelo con información sobre cada asociación. Estos métodos pueden ser utilizados por aplicaciones personalizadas para mostrar las relaciones de datos en una interfaz de usuario (UI), listas o elementos web de SharePoint.  
  
 Puede crear dos tipos de asociaciones en el diseñador BDC: asociaciones basada en claves externas y las asociaciones sin clave externas. Para obtener más información, consulte [crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md).  
  
### <a name="to-create-an-association-between-entities"></a>Para crear una asociación entre entidades  
  
1.  En el **BusinessDataConnectivity** pestaña de la **cuadro de herramientas**, elija la **asociación** elemento.  
  
2.  En el Diseñador de BDC, elija la entidad de origen y, a continuación, elija la entidad de destino.  
  
     El **Editor de asociaciones** aparece.  
  
3.  Si desea crear una asociación basada en clave externa, seleccione la **es una asociación de clave externa** casilla de verificación.  
  
    1.  En el **Id. de origen** columna de la **identificador de asignación** de tabla, elija el identificador situado junto a cada descriptor de tipos correspondiente que aparece en el **campo** columna.  
  
         Por ejemplo, en la **Id. de origen** columna, seleccione `ContactID` junto a la `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` descriptor de tipos y el `ReadItem.salesOrder.SalesOrder.ContactID` descriptor de tipos.  
  
4.  Si desea crear una asociación sin clave externa, desactive el **es una asociación de clave externa** casilla de verificación.  
  
5.  Elija el botón **Aceptar** .  
  
6.  En el Diseñador de BDC, aparece una línea que representa la asociación entre la entidad de origen y la entidad de destino.  
  
     Visual Studio agrega un método de navegación mediante asociaciones a la clase de servicio de la entidad de destino y la clase de servicio de la entidad de origen. Para obtener más información acerca de los métodos de navegación de asociación, vea [admite operaciones](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
7.  En el método de navegación mediante asociaciones de la entidad de origen, agregue código que devuelva una colección de entidades de destino.  
  
8.  En el método de navegación mediante asociaciones de la entidad de destino, agregue código que devuelva la entidad de origen relacionada.  
  
     Para obtener ejemplos de métodos de navegación mediante asociaciones, vea [crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md).  
  
## <a name="see-also"></a>Vea también  
 [Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md)   
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Información general de herramientas del diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)   
 [Cómo: definir el Descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Tutorial: Crear una lista externa en SharePoint mediante empresariales](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  