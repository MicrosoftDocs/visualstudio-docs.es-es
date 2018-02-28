---
title: "Cómo: incluir un ensamblado personalizado en una característica BDC | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 32554a0456c34a3c8b1d96c471fd7ae8e9221943
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Cómo: Incluir un ensamblado personalizado en una característica de BDC
  El proyecto puede hacer referencia a ensamblados de otros proyectos de la misma solución. Sin embargo, debe agregar estos ensamblados al archivo de características del proyecto mediante el **asignar al que hace referencia a LobSystems ensamblados** cuadro de diálogo.  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Para incluir un ensamblado personalizado en una característica de conectividad de datos profesionales (BDC)  
  
1.  En **el Explorador de soluciones**, elija la carpeta que contiene el modelo BDC.  
  
2.  En el menú **Ver** , haga clic en la **Ventana Propiedades**.  
  
3.  En el **propiedades** ventana, elija la **ensamblados** propiedad y, a continuación, en el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Elipse del Diseñador de")).  
  
     El **asignar al que hace referencia a LobSystems ensamblados** aparece el cuadro de diálogo.  
  
4.  En el **seleccione un ensamblado** lista, elija el ensamblado personalizado.  
  
    > [!NOTE]  
    >  Los ensamblados que solo aparecen en la **asignar al que hace referencia a LobSystems ensamblados** cuadro de diálogo si ha agregado una referencia al proyecto que contiene el ensamblado. Para obtener más información, consulte [Cómo: agregar o quitar referencias mediante el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  En el **propiedades de la referencia** grupo, abra la lista que aparece para el **LobSystem ámbito** propiedad, elija el sistema LOB de los métodos que utilizan el ensamblado personalizado y, a continuación, elijan el **Aceptar**  botón.  
  
    > [!NOTE]  
    >  Para depurar código en el ensamblado personalizado, debe agregar el ensamblado al paquete de solución. Para obtener más información, consulte [Cómo: agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: usar un archivo de recursos para especificar nombres localizados, propiedades y permisos](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Cómo: agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Cómo: crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  