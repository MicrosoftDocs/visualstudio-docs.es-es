---
title: 'Cómo: agregar un método Finder específico | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 732921b021d7887faf31dd3f602f5400c1d06a59
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985261"
---
# <a name="how-to-add-a-specific-finder-method"></a>Cómo: agregar un método Finder específico
  Puede devolver una única instancia de entidad creando un método de *buscador específico* . El servicio de conectividad a datos profesionales (BDC) ejecuta el método de buscador específico cuando un usuario elige una entidad en un elemento Web de datos profesionales o en una lista externa. Para obtener más información, vea [diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-specific-finder-method"></a>Para crear un método Finder específico

1. En el **Diseñador de BDC**, elija una entidad.

    Para obtener información sobre cómo agregar una entidad al **Diseñador de BDC** en Visual Studio, vea [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. En la barra de menús, elija **ver** > **otras ventanas**, **detalles del método BDC**.

    Se abre la ventana **detalles del método de BDC** . Para obtener más información acerca de esa ventana, consulte [información general sobre las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. En la lista **Agregar un método** , elija **crear método de buscador específico**.

    Visual Studio agrega los siguientes elementos al modelo. Estos elementos aparecen en la ventana **detalles del método de BDC** .

   - Un método

   - Parámetro de entrada para el método.

   - Parámetro devuelto para el método.

   - Un descriptor de tipo para cada parámetro.

   - Instancia de método para el método.

     Para obtener más información, vea [diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Abra la ventana **propiedades** de Visual Studio.

5. Configure el descriptor de tipo del parámetro devuelto como un descriptor de tipo de entidad. Para obtener información sobre cómo crear un descriptor de tipo de entidad, consulte [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > No tiene que realizar este paso si ha agregado un método Finder a la entidad. Visual Studio usa el descriptor de tipos que definió en el método Finder.

   > [!NOTE]
   > Si el campo identificador del tipo de entidad representa un campo de una tabla de base de datos que se genera automáticamente, establezca la propiedad de **solo lectura** del campo identificador en **true**.

6. En la ventana **detalles del método** , elija la instancia de método del método.

7. En la **ventana Propiedades**, establezca la propiedad **nombre del parámetro devuelto** en el nombre del parámetro devuelto del método. Para obtener más información sobre las propiedades de instancia de método, vea [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

8. En **Explorador de soluciones**, abra el menú contextual del archivo de código de servicio que se generó para la entidad y, a continuación, elija **Ver código**.

    El archivo de código de Entity Service se abre en el editor de código. Para obtener más información sobre el archivo de código de Entity Service, vea [crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).

9. Agregue código al método de buscador específico. Este código realiza las tareas siguientes:

   - Recupera un registro de un origen de datos.

   - Devuelve una entidad al servicio BDC.

     En el ejemplo siguiente se devuelve un contacto de la base de datos de ejemplo AdventureWorks para SQL Server.

     > [!NOTE]
     > Reemplace el valor del campo `ServerName` por el nombre del servidor.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="see-also"></a>Vea también
- [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Cómo: agregar un método de eliminación](../sharepoint/how-to-add-a-deleter-method.md)
- [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Introducción a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)
