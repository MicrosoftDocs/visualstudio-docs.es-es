---
title: "Cómo: usar un archivo de recursos para especificar nombres localizados, propiedades y permisos | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 144d81b2835479ee8cfdff0657814070cff813db
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Cómo: Usar un archivo de recursos para especificar nombres, propiedades y permisos localizados
  Mediante el uso de un archivo de recursos, puede proporcionar los nombres traducidos, definir propiedades y aplicar permisos tor objetos que se definen en un modelo de conectividad de datos profesionales (BDC). Para especificar esta información, agregue un **recurso de conectividad a datos empresariales** elemento a un proyecto que contiene un **modelo de conectividad a datos empresariales** elemento. A continuación, especifique los nombres, propiedades y permisos mediante la edición de XML para el archivo de recursos.  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Para agregar un archivo de recursos BDC a un proyecto de SharePoint  
  
1.  En **el Explorador de soluciones**, expanda la carpeta del proyecto de SharePoint y, a continuación, elija la carpeta que contiene el modelo BDC.  
  
2.  En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
3.  Expanda el **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
4.  En el **Agregar nuevo elemento** diálogo cuadro, elija **elemento de recurso de conexión de datos de negocio**.  
  
5.  En el **nombre** cuadro, especifique el nombre del archivo de recursos y, a continuación, elija la **agregar** botón.  
  
     Un archivo de recursos que tiene la extensión .bdcr se agrega al proyecto y abre para su edición.  
  
6.  Agregue el código XML para definir los nombres traducidos, propiedades y permisos que se desea aplicar el modelo BDC.  
  
     Para obtener información sobre cómo definir estos elementos, vea [modelo y archivos de recursos](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Cómo: crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Cómo: incluir un ensamblado personalizado en una característica BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  