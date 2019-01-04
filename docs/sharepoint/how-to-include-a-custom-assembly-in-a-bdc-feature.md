---
title: Procedimiento Incluir un ensamblado personalizado en una característica de BDC | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3b53b7c8b5cf4dd2c13adbb53a9724a8adaf2328
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53919526"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Procedimiento Incluir un ensamblado personalizado en una característica de BDC
  El proyecto puede hacer referencia a ensamblados desde otros proyectos en la misma solución. Sin embargo, debe agregar estos ensamblados al archivo de características del proyecto mediante el **asignar al que hace referencia a LobSystems ensamblados** cuadro de diálogo.  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Para incluir un ensamblado personalizado en una característica de conectividad (BDC) de datos de negocio
  
1.  En **el Explorador de soluciones**, elija la carpeta que contiene el modelo BDC.  
  
2.  En el menú **Ver** , haga clic en la **Ventana Propiedades**.  
  
3.  En el **propiedades** ventana, elija el **ensamblados** propiedad y, a continuación, en el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Elipse del diseñador")).  
  
     El **asignar al que hace referencia a LobSystems ensamblados** aparece el cuadro de diálogo.  
  
4.  En el **seleccione un ensamblado** lista, elija el ensamblado personalizado.  
  
    > [!NOTE]  
    >  Los ensamblados que solo aparecen en la **asignar al que hace referencia a LobSystems ensamblados** cuadro de diálogo si se ha agregado una referencia al proyecto que contiene el ensamblado. Para obtener más información, vea [Cómo: Agregar o quitar referencias mediante el cuadro de diálogo Agregar referencia](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  En el **propiedades de la referencia** agrupar, abra la lista que aparece para la **ámbito de LobSystem** propiedad, elija el sistema LOB de los métodos que utilizan el ensamblado personalizado y, a continuación, elijan el **Aceptar**  botón.  
  
    > [!NOTE]  
    >  Para depurar código en el ensamblado personalizado, debe agregar el ensamblado al paquete de solución. Para obtener más información, vea [Cómo: Agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## <a name="see-also"></a>Vea también
 [Cómo: Use un archivo de recursos para especificar los permisos, propiedades y nombres localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Cómo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Datos de negocio Integragte en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
