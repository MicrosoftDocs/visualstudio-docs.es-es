---
title: 'Cómo: incluir un ensamblado personalizado en una característica de BDC | Microsoft Docs'
description: Incluir ensamblados personalizados en una característica de conectividad a datos profesionales (BDC) para que el proyecto pueda hacer referencia a ensamblados de otros proyectos de la misma solución.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7a2a0109faca4da5406b45b4d606ae8a5cd0685
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903473"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Cómo: incluir un ensamblado personalizado en una característica de BDC
  El proyecto puede hacer referencia a ensamblados de otros proyectos de la misma solución. Sin embargo, debe agregar estos ensamblados al archivo de características del proyecto mediante el cuadro de diálogo **asignar los ensamblados a los que se hace referencia a LobSystems** .

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Para incluir un ensamblado personalizado en una característica de conectividad a datos profesionales (BDC)

1. En **Explorador de soluciones**, elija la carpeta que contiene el modelo BDC.

2. En el menú **Ver** , haga clic en **Ventana de propiedades**.

3. En la ventana **propiedades** , elija la propiedad **ensamblados** y, a continuación, el botón de puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")).

     Aparece el cuadro de diálogo **asignar los ensamblados a los que se hace referencia a LobSystems** .

4. En la lista **seleccionar un ensamblado** , elija el ensamblado personalizado.

    > [!NOTE]
    > Los ensamblados solo aparecen en el cuadro de diálogo **asignar ensamblados de referencia a LobSystems** si ha agregado una referencia al proyecto que contiene el ensamblado. Para obtener más información, vea [Cómo: agregar o quitar referencias mediante el cuadro de diálogo Agregar referencia](/previous-versions/wkze6zky(v=vs.140)).

5. En el grupo **propiedades de referencia** , abra la lista que aparece para la propiedad ámbito de **LobSystem** , elija el sistema de LOB de los métodos que usan el ensamblado personalizado y, a continuación, elija el botón **Aceptar** .

    > [!NOTE]
    > Para depurar el código del ensamblado personalizado, debe agregar el ensamblado al paquete de solución. Para obtener más información, consulte [Cómo: agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>Consulte también
- [Cómo: para usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Cómo: para agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Creación de un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Cómo: para crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Integragte datos empresariales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)