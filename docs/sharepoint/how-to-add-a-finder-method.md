---
title: "Cómo: agregar un método Finder | Documentos de Microsoft"
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
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c2c7bf2eed200b8ed223f266ca35b5af90862cd6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-finder-method"></a>Cómo: Agregar un método Finder
  Para habilitar el servicio de conectividad a datos profesionales mostrar una lista de entidades en un elemento web o una lista, debe crear un *buscador* método. Un método Finder es un método especial que devuelve una colección de instancias de entidad. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Para crear un método Finder  
  
1.  En el Diseñador de BDC, elija una entidad.  
  
     Para obtener más información, consulte [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  En la barra de menús, elija **vista**, **otras ventanas**, **detalles del método de BDC**.  
  
     El **detalles del método de BDC** abre la ventana. Para obtener más información sobre la **detalles del método de BDC** ventana, consulte [herramientas información general del diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  En el **agregar un método** elija **crear método Finder**.  
  
     Visual Studio agrega un método, un parámetro de retorno y un descriptor de tipos.  
  
4.  Configure el descriptor de tipo como un descriptor de tipo de colección de entidades. Para obtener más información sobre cómo crear un descriptor de tipo de colección de entidades, vea [Cómo: definir el Descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  No es necesario realizar este paso si ha agregado un método Finder específico a la entidad. Visual Studio utiliza el descriptor de tipo que ha definido en el método Finder específico.  
  
5.  En **el Explorador de soluciones**, abra el menú contextual del servicio archivo de código que se generó para la entidad y, a continuación, elija **ver código**. Para obtener más información sobre el archivo de código de servicio, consulte [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Agregue código al método Finder. Este código realiza las tareas siguientes:  
  
    -   Recupera datos de un origen de datos.  
  
    -   Devuelve una lista de entidades al servicio BDC.  
  
     En el ejemplo siguiente se devuelve una colección de `Contact` entidades mediante el uso de datos de la base de datos de ejemplo de AdventureWorks para SQL Server.  
  
    > [!NOTE]  
    >  Sustituya el valor de la `ServerName` campo con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>Vea también  
 [Información general de herramientas del diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)  
  
  