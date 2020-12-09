---
title: 'Cómo: agregar un método Finder | Microsoft Docs'
description: Agregue un método Finder en Visual Studio, que habilita el servicio de conectividad a datos profesionales (BDC) para mostrar una lista de entidades en un elemento Web o lista de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b7e2bb74278194878ed4496c12c918707cdc1e6e
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915094"
---
# <a name="how-to-add-a-finder-method"></a>Cómo: agregar un método Finder
  Para habilitar el servicio de conectividad a datos profesionales (BDC) para mostrar una lista de entidades en un elemento Web o lista, debe crear un método de *buscador* . Un método Finder es un método especial que devuelve una colección de instancias de entidad. Para obtener más información, vea [diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Para crear un método Finder

1. En el **Diseñador de BDC**, elija una entidad.

    Para obtener más información, vea [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. En la barra de menús, elija **Ver**  >  **otros**  >  **detalles del método BDC** de Windows.

    Se abre la ventana **detalles del método de BDC** . Para obtener más información acerca de la ventana **detalles del método de BDC** , consulte información general sobre las herramientas de diseño del [modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. En la lista **Agregar un método** , elija **crear método de buscador**.

    Visual Studio agrega un método, un parámetro de retorno y un descriptor de tipos.

4. Configure el descriptor de tipo como un descriptor de tipo de colección de entidades. Para obtener más información sobre cómo crear un descriptor de tipo de colección de entidades, vea [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > No es necesario que realice este paso si ha agregado un método Finder específico a la entidad. Visual Studio usa el descriptor de tipos que definió en el método Finder específico.

5. En **Explorador de soluciones**, abra el menú contextual del archivo de código de servicio que se generó para la entidad y, a continuación, elija **Ver código**. Para obtener más información sobre el archivo de código de servicio, vea [crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Agregue código al método Finder. Este código realiza las tareas siguientes:

   - Recupera datos de un origen de datos.

   - Devuelve una lista de entidades al servicio BDC.

     En el ejemplo siguiente se devuelve una colección de `Contact` entidades utilizando los datos de la base de datos de ejemplo AdventureWorks para SQL Server.

   > [!NOTE]
   > Reemplace el valor del `ServerName` campo por el nombre del servidor.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>Consulte también
- [Introducción a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Cómo: agregar un método de eliminación](../sharepoint/how-to-add-a-deleter-method.md)
- [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)
