---
title: 'Cómo: agregar un método Creator | Microsoft Docs'
description: Sepa cómo agregar un método Creator, que agrega nuevos datos al origen de datos de una entidad en el servicio de conectividad a datos profesionales (BDC) de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 790b4265b232c71ff3e0613cffcb45e710081fa3
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915458"
---
# <a name="how-to-add-a-creator-method"></a>Cómo: agregar un método Creator
  Un método Creator agrega nuevos datos al origen de datos de una entidad. El servicio de conectividad a datos profesionales (BDC) llama a este método cuando los usuarios eligen el botón **nuevo elemento** de la **cinta** de opciones de una lista basada en el modelo. Para obtener más información, vea [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-add-a-creator-method"></a>Para agregar un método Creator

1. En el **Diseñador de BDC**, elija una entidad.

2. En la barra de menús, elija **Ver**  >  **otros**  > **detalles del método BDC** de Windows.

    Se abre la ventana **detalles del método de BDC** . Para obtener más información acerca de esa ventana, consulte [información general sobre las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. En la lista **Agregar un método** , elija **crear método Creator**.

    Visual Studio agrega los siguientes elementos al modelo y estos elementos aparecen en la ventana **detalles del método de BDC** .

   - Un método denominado **Create**.

   - Parámetro de entrada para el método.

   - Parámetro devuelto para el método.

   - Descriptores de tipos para los parámetros.

   - Instancia de método para el método.

     Para obtener más información, vea [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

4. En **Explorador de soluciones**, abra el menú contextual del archivo de código de servicio que se generó para la entidad y, a continuación, elija **Ver código**.

    El archivo de código de Entity Service se abre en el editor de código. Para obtener más información sobre el archivo de código de Entity Service, vea [crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Agregue código al método Creator que agrega los datos al origen de datos. En el siguiente ejemplo se agrega un contacto a la base de datos de ejemplo AdventureWorks para SQL Server.

   > [!NOTE]
   > Reemplace el valor del `ServerName` campo por el nombre del servidor.

    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]

## <a name="see-also"></a>Consulte también
- [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Cómo: agregar un método de eliminación](../sharepoint/how-to-add-a-deleter-method.md)
- [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Introducción a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)
