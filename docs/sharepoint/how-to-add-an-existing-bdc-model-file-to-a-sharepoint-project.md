---
title: 'Cómo: agregar un archivo de modelo BDC existente a un proyecto de SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bda78d33a5b49d936fb632e78472c91ab1230ba5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922619"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Cómo: agregar un archivo de modelo BDC existente a un proyecto de SharePoint
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
 [Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Cómo: crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Cómo: usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Cómo: incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
 
