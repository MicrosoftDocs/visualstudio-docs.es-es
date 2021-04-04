---
title: 'Cómo: agregar una entidad a un modelo | Microsoft Docs'
description: Agregue una entidad a un modelo agregando un control de entidad desde el cuadro de herramientas de Visual Studio al diseñador de conectividad a datos profesionales (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94d34e6a623438cd0e2d63d74ee2321841a0582a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216779"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Cómo: agregar una entidad a un modelo
  Para crear una entidad, agregue un control de entidad desde el **cuadro de herramientas** de Visual Studio al diseñador de conectividad a datos profesionales (BDC).

### <a name="to-add-an-entity-to-the-model"></a>Para agregar una entidad al modelo

1. Cree un proyecto de BDC o abra un proyecto de BDC existente. Para obtener más información, vea [Creación de un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).

2. En el **cuadro de herramientas**, en el grupo **BusinessDataCatalog** , agregue un control de **entidad** al diseñador.

     La nueva entidad aparece en el diseñador. Visual Studio agrega un `<Entity>` elemento al XML del archivo de modelo BDC en el proyecto. Para obtener más información sobre los atributos de un elemento de entidad, vea [Entity](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14)).

3. En el diseñador, abra el menú contextual de la entidad, elija **Agregar** y, a continuación, elija **identificador**.

     Aparece un nuevo identificador en la entidad.

    > [!NOTE]
    > Puede cambiar el nombre de la entidad y el identificador en la ventana **propiedades** .

4. Defina los campos de la entidad en una clase. Puede Agregar una nueva clase al proyecto o utilizar una clase existente creada con otras herramientas, como el Object Relational Designer (Object Relational Designer). En el ejemplo siguiente se muestra una clase de entidad denominada contact.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs" id="Snippet1":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb" id="Snippet1":::

## <a name="see-also"></a>Consulte también
- [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Cómo: agregar un método de eliminación](../sharepoint/how-to-add-a-deleter-method.md)
- [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)
