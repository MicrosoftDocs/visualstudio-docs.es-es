---
title: 'Cómo: agregar un método Finder específico | Microsoft Docs'
description: Obtenga una instancia de entidad agregando un método de buscador. El servicio BDC llama al método cuando un usuario elige una entidad en un elemento Web de datos profesionales o en una lista externa.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 87f5b0cf86178b88b1611f4b0ce8a4bbacde780e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216805"
---
# <a name="how-to-add-a-specific-finder-method"></a>Cómo: agregar un método Finder específico
  Puede devolver una única instancia de entidad creando un método de *buscador específico* . El servicio de conectividad a datos profesionales (BDC) ejecuta el método de buscador específico cuando un usuario elige una entidad en un elemento Web de datos profesionales o en una lista externa. Para obtener más información, vea [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-specific-finder-method"></a>Para crear un método Finder específico

1. En el **Diseñador de BDC**, elija una entidad.

    Para obtener información sobre cómo agregar una entidad al **Diseñador de BDC** en Visual Studio, vea [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. En la barra de menús, elija **Ver**  >  **otras ventanas**, **detalles del método BDC**.

    Se abre la ventana **detalles del método de BDC** . Para obtener más información acerca de esa ventana, consulte [información general sobre las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. En la lista **Agregar un método** , elija **crear método de buscador específico**.

    Visual Studio agrega los siguientes elementos al modelo. Estos elementos aparecen en la ventana **detalles del método de BDC** .

   - Un método

   - Parámetro de entrada para el método.

   - Parámetro devuelto para el método.

   - Un descriptor de tipo para cada parámetro.

   - Instancia de método para el método.

     Para obtener más información, vea [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

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
     > Reemplace el valor del `ServerName` campo por el nombre del servidor.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet3":::

## <a name="see-also"></a>Consulte también
- [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Cómo: agregar un método de eliminación](../sharepoint/how-to-add-a-deleter-method.md)
- [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Introducción a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)
