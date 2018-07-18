---
title: 'Cómo: agregar un método Finder | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3c7233f344282b5ce5793f7b6733e5e657534023
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756985"
---
# <a name="how-to-add-a-finder-method"></a>Cómo: agregar un método Finder
  Para habilitar el servicio de conectividad de datos profesionales (BDC) mostrar una lista de entidades en una lista o un elemento web, debe crear un *buscador* método. Un método Finder es un método especial que devuelve una colección de instancias de entidad. Para obtener más información, consulte [diseñar un modelo de conectividad de datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Para crear un método Finder  
  
1.  En el **Diseñador de BDC**, elegir una entidad.  
  
     Para obtener más información, consulte [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  En la barra de menús, elija **vista** > **Other Windows** > **detalles del método de BDC**.  
  
     El **detalles del método de BDC** abre la ventana. Para obtener más información sobre la **detalles del método de BDC** ventana, consulte [información general de las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  En el **agregue un método** elija **crear método Finder**.  
  
     Visual Studio agrega un método, un parámetro de retorno y un descriptor de tipos.  
  
4.  Configure el descriptor de tipos como un descriptor de tipo de colección de entidades. Para obtener más información sobre cómo crear un descriptor de tipo de colección de entidades, vea [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  No es necesario realizar este paso si ha agregado un método Finder específico a la entidad. Visual Studio utiliza el descriptor de tipos que definió en el método de buscador específico.  
  
5.  En **el Explorador de soluciones**, abra el menú contextual del servicio archivo de código que se generó para la entidad y, a continuación, elija **ver código**. Para obtener más información sobre el archivo de código de servicio, consulte [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Agregue código al método Finder. Este código realiza las tareas siguientes:  
  
    -   Recupera datos de un origen de datos.  
  
    -   Devuelve una lista de entidades para el servicio BDC.  
  
     El ejemplo siguiente devuelve una colección de `Contact` entidades mediante el uso de datos de la base de datos de ejemplo AdventureWorks para SQL Server.  
  
    > [!NOTE]  
    >  Reemplace el valor de la `ServerName` campo con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>Vea también
 [Introducción a las herramientas de diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)  
  
  
