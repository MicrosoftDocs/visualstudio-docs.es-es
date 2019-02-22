---
title: Procedimiento Agregar un archivo de modelo BDC existente a un proyecto de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c10dcf48e5c047778b86c524b35b4e1d5d8cc8a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614628"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Filtrar Agregar un archivo de modelo BDC existente a un proyecto de SharePoint
  Puede personalizar, empaquetar y volver a implementar un modelo de conectividad de datos profesionales (BDC) mediante Visual Studio para agregar el archivo de modelo (*.bdcm*) a cualquier proyecto de la granja de servidores de SharePoint. Para obtener más información, consulte [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Para agregar un archivo de modelo BDC a un proyecto de SharePoint

1. En **el Explorador de soluciones**, elija la carpeta para un proyecto de SharePoint.

2. En la barra de menús, elija **proyecto** > **Agregar elemento existente**.

3. En el **Agregar elemento existente** cuadro de diálogo, vaya a la ubicación del archivo de definición del modelo que desea agregar al proyecto, elija el archivo y, a continuación, elija el **agregar** botón.

    Si el modelo no define un *sistema de línea de negocio (LOB) de tipo de ensamblado .NET*, el **LobSystem de ensamblado .NET agregar** abre el cuadro de diálogo.

4. Si aparece el cuadro de diálogo, realice uno de los pasos siguientes:

   - Si desea escribir código personalizado y usar un diseñador para definir los metadatos del modelo importado, elija el **Sí** botón, el sistema de nombres y, a continuación, elija el **Aceptar** botón.

   - En caso contrario, elija el **No** botón y, a continuación, elija el **Aceptar** botón.

     El **modelo de conectividad a datos empresariales** elemento se agrega al proyecto.

## <a name="see-also"></a>Vea también
- [Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Cómo: Use un archivo de recursos para especificar los permisos, propiedades y nombres localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Cómo: Incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
