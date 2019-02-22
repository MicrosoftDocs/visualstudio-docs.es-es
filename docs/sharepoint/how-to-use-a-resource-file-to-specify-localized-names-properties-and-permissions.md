---
title: Procedimiento Use un archivo de recursos para especificar nombres localizados, propiedades y permisos | Documentos de Microsoft
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
ms.openlocfilehash: 9014b344e030f3763037395f5fb96d446c0132f0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621557"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Filtrar Use un archivo de recursos para especificar los permisos, propiedades y nombres localizados
  Mediante el uso de un archivo de recursos, puede proporcionar nombres localizados, definir propiedades y aplicar permisos tor objetos que se definen en un modelo de conectividad de datos profesionales (BDC). Para especificar esta información, agregue un **recurso conectividad a datos profesionales** elemento a un proyecto que contiene un **modelo de conectividad a datos empresariales** elemento. A continuación, especifique los nombres, propiedades y permisos mediante la edición de XML para el archivo de recursos.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Para agregar un archivo de recursos BDC a un proyecto de SharePoint

1.  En **el Explorador de soluciones**, expanda la carpeta del proyecto de SharePoint y, a continuación, elija la carpeta que contiene el modelo BDC.

2.  En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

3.  Expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.

4.  En el **Agregar nuevo elemento** diálogo cuadro, elija **elemento de recurso de conexión de datos de negocio**.

5.  En el **nombre** cuadro, especifique el nombre del archivo de recursos y, a continuación, elija el **agregar** botón.

     Un archivo de recursos que tiene la extensión .bdcr se agrega al proyecto y abre para su edición.

6.  Agregue el código XML para definir los nombres localizados, propiedades y los permisos que desea aplicar el modelo BDC.

     Para obtener información sobre cómo definir estos elementos, vea [modelo y los archivos de recursos](http://go.microsoft.com/fwlink/?LinkID=169283).

## <a name="see-also"></a>Vea también
- [Cómo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Cómo: Incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
