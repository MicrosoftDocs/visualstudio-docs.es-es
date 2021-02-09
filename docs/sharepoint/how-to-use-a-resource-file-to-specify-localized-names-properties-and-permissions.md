---
title: Cómo usar un archivo de recursos en un proyecto de SharePoint | Microsoft Docs
titleSuffix: ''
description: Use un archivo de recursos en un proyecto de SharePoint para poder proporcionar nombres localizados, definir propiedades y aplicar permisos para los objetos definidos en un modelo BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 49546d11dbf4f19bb2fd826ace2850468f780d13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851561"
---
# <a name="how-to-use-a-resource-file-in-a-sharepoint-project"></a>Cómo usar un archivo de recursos en un proyecto de SharePoint

  Mediante el uso de un archivo de recursos, puede proporcionar nombres localizados, definir propiedades y aplicar permisos de los objetos que se definen en un modelo de conectividad a datos profesionales (BDC). Para especificar esta información, agregue un elemento de **recurso de conectividad de datos profesionales** a un proyecto que contenga un elemento de **modelo de conectividad a datos profesionales** . A continuación, especifique los nombres, propiedades y permisos editando el XML para el archivo de recursos.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Para agregar un archivo de recursos de BDC a un proyecto de SharePoint

1. En **Explorador de soluciones**, expanda la carpeta del proyecto de SharePoint y, a continuación, elija la carpeta que contiene el modelo BDC.

2. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

3. Expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

4. En el cuadro de diálogo **Agregar nuevo elemento** , elija **elemento de recurso de conectividad a datos profesionales**.

5. En el cuadro **nombre** , especifique el nombre del archivo de recursos y, a continuación, elija el botón **Agregar** .

     Un archivo de recursos que tiene la extensión. bdcr se agrega al proyecto y se abre para su edición.

6. Agregue XML para definir los nombres localizados, las propiedades y los permisos que desea aplicar al modelo BDC.

     Para obtener información sobre cómo definir estos elementos, vea [archivos de modelo y de recursos](/previous-versions/office/developer/sharepoint-2010/aa674515(v=office.14)).

## <a name="see-also"></a>Vea también
- [Cómo: para agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Creación de un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Cómo: para crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Cómo: incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
