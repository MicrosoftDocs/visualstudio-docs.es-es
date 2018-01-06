---
title: "Cómo: agregar un método Finder específico | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6a5dbff1d4a4c739ce8ecab0807e2d74c62f999e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-specific-finder-method"></a>Cómo: Agregar un método Finder específico
  Puede devolver una instancia de entidad única creando un *método Finder específico* método. El servicio de conectividad de datos profesionales (BDC) ejecuta el método Finder específico cuando un usuario elige una entidad en una lista externa o un elemento web datos económicos. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-specific-finder-method"></a>Para crear un método Finder específico  
  
1.  En el Diseñador de BDC, elija una entidad.  
  
     Para obtener información sobre cómo agregar una entidad al diseñador BDC en Visual Studio, vea [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  En la barra de menús, elija **vista**, **otras ventanas**, **detalles del método de BDC**.  
  
     El **detalles del método de BDC** abre la ventana. Para obtener más información acerca de esta ventana, consulte [herramientas información general del diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  En el **agregar un método** elija **crear método Finder específico**.  
  
     Visual Studio agrega los siguientes elementos al modelo. Estos elementos aparecen en la **detalles del método de BDC** ventana.  
  
    -   Un método  
  
    -   Un parámetro de entrada para el método.  
  
    -   Un parámetro de valor devuelto del método.  
  
    -   Un descriptor de tipo para cada parámetro.  
  
    -   Una instancia de método para el método.  
  
     Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Abra Visual Studio **propiedades** ventana.  
  
5.  Configure el descriptor de tipo del parámetro devuelto como un descriptor de tipo de entidad. Para obtener información sobre cómo crear un descriptor de tipo de entidad, vea [Cómo: definir el Descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  No tienes que realizar este paso si ha agregado un método Finder a la entidad. Visual Studio utiliza el descriptor de tipo definido en el método de buscador.  
  
    > [!NOTE]  
    >  Si el campo de identificador del tipo de entidad representa un campo en una tabla de base de datos que se genera automáticamente, establezca la **de sólo lectura** propiedad del campo de identificador a **True**.  
  
6.  En el **detalles del método** ventana, elija la instancia de método del método.  
  
7.  En el **ventana propiedades**, establezca el **devolver el nombre del parámetro** propiedad en el nombre del parámetro devuelto del método. Para obtener más información acerca de las propiedades de la instancia de método, consulte [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8.  En **el Explorador de soluciones**, abra el menú contextual del servicio archivo de código que se generó para la entidad y, a continuación, elija **ver código**.  
  
     El archivo de código del servicio de entidad se abre en el Editor de código. Para obtener más información sobre el archivo de código del servicio de entidad, vea [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Agregue código al método Finder específico. Este código realiza las tareas siguientes:  
  
    -   Recupera un registro de un origen de datos.  
  
    -   Devuelve una entidad al servicio BDC.  
  
     En el ejemplo siguiente se devuelve un contacto de la base de datos de ejemplo de AdventureWorks para SQL Server.  
  
    > [!NOTE]  
    >  Sustituya el valor de la `ServerName` campo con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>Vea también  
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Información general de herramientas del diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)  
  
  