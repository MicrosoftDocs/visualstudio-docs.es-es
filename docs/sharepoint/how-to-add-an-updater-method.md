---
title: Procedimiento Agregar un método Updater | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8a68ed8809b30444829dc09bb5c1fcb2386c4a92
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872523"
---
# <a name="how-to-add-an-updater-method"></a>Procedimiento Agregar un método Updater
  Puede permitir a los usuarios actualizar los datos empresariales en una lista externa de SharePoint mediante la creación de un *actualizador* método. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-an-updater-method"></a>Para crear un método Updater  
  
1. En el Diseñador de BDC, elija una entidad.  
  
2. En la barra de menús, elija **vista** > **Other Windows** > **detalles del método de BDC**.  
  
    Se abre la ventana de detalles del método de BDC. Para obtener más información acerca de esta ventana, consulte [información general de las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. En el **agregue un método** elija **crear método Updater**.  
  
    Visual Studio agrega los siguientes elementos al modelo. Estos elementos aparecen en la ventana de detalles del método de BDC.  
  
   - Un método que se denomina **actualización**.  
  
   - Un parámetro de entrada para el método.  
  
   - Un descriptor de tipos para el parámetro. De forma predeterminada, Visual Studio utiliza el descriptor de tipos de entidad que ha definido para el método de buscador (por ejemplo: Póngase en contacto con).  
  
   - Una instancia de método para el método.  
  
     Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
   > [!NOTE]  
   >  Si el identificador del tipo de entidad representa un campo en una tabla de base de datos que se genera automáticamente, establezca la **campo Pre-Updater** propiedad **True**.  
  
4. En **el Explorador de soluciones**, abra el menú contextual del servicio archivo de código que se generó para la entidad y, a continuación, elija **ver código**.  
  
    Se abre el archivo de código del servicio de entidad en el **Editor de código**. Para obtener más información acerca de dicho archivo, consulte [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Agregue código al método Update para actualizar los datos. El ejemplo siguiente actualiza la información de un contacto en la base de datos de ejemplo AdventureWorks para SQL Server.  
  
   > [!NOTE]  
   >  Reemplace el valor de la `ServerName` campo con el nombre del servidor.  
  
    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>Vea también
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Introducción a las herramientas de diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)  
