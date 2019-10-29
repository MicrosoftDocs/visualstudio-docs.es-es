---
title: 'Cómo: usar un archivo de recursos para especificar nombres, propiedades y permisos localizados | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fa2fec260921d66328b2c16075d44b38686c08de
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982554"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Cómo: usar un archivo de recursos para especificar nombres, propiedades y permisos localizados
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
- [Cómo: agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Cómo: crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Cómo: incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
