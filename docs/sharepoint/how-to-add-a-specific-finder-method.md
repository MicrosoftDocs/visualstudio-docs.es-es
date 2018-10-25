---
title: 'Cómo: agregar un método Finder específico | Microsoft Docs'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8005728d29c38e32d55f01e42d2666c69112b3f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886494"
---
# <a name="how-to-add-a-specific-finder-method"></a>Cómo: agregar un método Finder específico
  Puede devolver una instancia de entidad única mediante la creación de un *buscador específico* método. El servicio de conectividad de datos profesionales (BDC) ejecuta el método de buscador específico cuando un usuario elige una entidad en un elemento web de datos de negocio o una lista externa. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-specific-finder-method"></a>Para crear un método Finder específico
  
1. En el **Diseñador de BDC**, elegir una entidad.  
  
    Para obtener información sobre cómo agregar una entidad a la **Diseñador de BDC** en Visual Studio, consulte [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2. En la barra de menús, elija **vista** > **Other Windows**, **detalles del método de BDC**.  
  
    El **detalles del método de BDC** abre la ventana. Para obtener más información acerca de esta ventana, consulte [información general de las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. En el **agregue un método** elija **crear método Finder específico**.  
  
    Visual Studio agrega los siguientes elementos al modelo. Estos elementos aparecen en la **detalles del método de BDC** ventana.  
  
   - Un método  
  
   - Un parámetro de entrada para el método.  
  
   - Un parámetro de valor devuelto del método.  
  
   - Un descriptor de tipo para cada parámetro.  
  
   - Una instancia de método para el método.  
  
     Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4. Abra Visual Studio **propiedades** ventana.  
  
5. Configure el descriptor de tipo del parámetro devuelto como un descriptor de tipo de entidad. Para obtener información sobre cómo crear un descriptor de tipo de entidad, vea [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
   > [!NOTE]  
   >  No tiene que realizar este paso si ha agregado un método Finder para la entidad. Visual Studio utiliza el descriptor de tipos que definió en el método Finder.  
  
   > [!NOTE]  
   >  Si el campo de identificador del tipo de entidad representa un campo en una tabla de base de datos que se genera automáticamente, establezca la **de sólo lectura** propiedad del campo de identificador a **True**.  
  
6. En el **detalles del método** ventana, elija la instancia de método del método.  
  
7. En el **ventana propiedades**, establezca el **devolver el nombre del parámetro** propiedad en el nombre del parámetro devuelto del método. Para obtener más información acerca de las propiedades de la instancia de método, consulte [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8. En **el Explorador de soluciones**, abra el menú contextual del servicio archivo de código que se generó para la entidad y, a continuación, elija **ver código**.  
  
    El archivo de código del servicio de entidad se abre en el Editor de código. Para obtener más información sobre el archivo de código del servicio de entidad, vea [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Agregue código al método Finder específico. Este código realiza las tareas siguientes:  
  
   - Recupera un registro de un origen de datos.  
  
   - Devuelve una entidad para el servicio BDC.  
  
     En el ejemplo siguiente se devuelve un contacto de la base de datos de ejemplo AdventureWorks para SQL Server.  
  
     > [!NOTE]  
     >  Reemplace el valor de la `ServerName` campo con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>Vea también
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Introducción a las herramientas de diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)  
  
