---
title: 'Cómo: agregar un archivo de modelo BDC existente a un proyecto de SharePoint | Microsoft Docs'
titleSuffix: ''
description: Agregue un archivo de modelo de conectividad a datos profesionales (BDC) existente a un proyecto de SharePoint en Visual Studio, para que pueda personalizar, empaquetar y volver a implementar un modelo BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af0768b4834eb1cad3654b6d74ee8f02cf464245
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882679"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Cómo: para agregar un archivo de modelo BDC existente a un proyecto de SharePoint
  Puede personalizar, empaquetar y volver a implementar un modelo de conectividad a datos profesionales (BDC) mediante Visual Studio para agregar el archivo de modelo (*. bdcm*) a cualquier proyecto de granja de SharePoint. Para obtener más información, vea [Creación de un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Para agregar un archivo de modelo BDC a un proyecto de SharePoint

1. En **Explorador de soluciones**, elija la carpeta de un proyecto de SharePoint.

2. En la barra de menús, elija **proyecto**  >  **Agregar elemento existente**.

3. En el cuadro de diálogo **Agregar elemento existente** , vaya a la ubicación del archivo de definición de modelo que desee agregar al proyecto, elija el archivo y, a continuación, elija el botón **Agregar** .

    Si el modelo no define un *sistema de línea de negocio (LOB) del tipo ensamblado .net*, se abre el cuadro de diálogo **Agregar LobSystem de ensamblado .net** .

4. Si aparece el cuadro de diálogo, realice uno de los pasos siguientes:

   - Si desea escribir código personalizado y usar un diseñador para definir los metadatos para el modelo importado, elija el botón **sí** , asigne un nombre al sistema y, a continuación, elija el botón **Aceptar** .

   - En caso contrario, elija el botón **no** y, a continuación, elija el botón **Aceptar** .

     El elemento de **modelo de conectividad a datos profesionales** se agrega al proyecto.

## <a name="see-also"></a>Vea también
- [Creación de un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Cómo: para crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Cómo: para usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Cómo: incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
