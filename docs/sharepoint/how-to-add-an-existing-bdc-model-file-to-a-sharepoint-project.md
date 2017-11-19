---
title: "Cómo: agregar un archivo de modelo BDC existente a un proyecto de SharePoint | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.ImportDialog
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
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d0ae7190d0b55dec593e8d9f7c20542d5a7d5bc6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Cómo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint
  Puede personalizar, empaquetar y volver a implementar un modelo de conectividad de datos profesionales (BDC) mediante Visual Studio para agregar el archivo de modelo (bdcm) a cualquier proyecto de la granja de servidores de SharePoint. Para obtener más información, consulte [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Para agregar un archivo de modelo BDC a un proyecto de SharePoint  
  
1.  En **el Explorador de soluciones**, elija la carpeta de un proyecto de SharePoint.  
  
2.  En la barra de menús, elija **proyecto**, **Agregar elemento existente**.  
  
3.  En el **Agregar elemento existente** cuadro de diálogo, vaya a la ubicación del archivo de definición del modelo que desea agregar al proyecto, elija el archivo y, a continuación, elija la **agregar** botón.  
  
     Si el modelo no se define un *sistema de línea de negocio (LOB) del tipo de ensamblado .NET*, el **LobSystem de ensamblado .NET agregar** abre el cuadro de diálogo.  
  
4.  Si aparece el cuadro de diálogo, realice uno de los siguientes pasos:  
  
    -   Si desea escribir código personalizado y utilizar un diseñador para definir los metadatos del modelo importado, elija la **Sí** botón, el sistema de nombres y, a continuación, elija la **Aceptar** botón.  
  
    -   En caso contrario, elija la **No** botón y, a continuación, elija la **Aceptar** botón.  
  
     El **modelo de conectividad a datos empresariales** elemento se agrega al proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Cómo: crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Cómo: usar un archivo de recursos para especificar nombres localizados, propiedades y permisos](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Cómo: incluir un ensamblado personalizado en una característica BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  