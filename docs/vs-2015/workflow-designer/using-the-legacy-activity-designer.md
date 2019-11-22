---
title: Using the Legacy Activity Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a13aeeb3394ee6b8896376c0e7d520b90fb56fa6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302821"
---
# <a name="using-the-legacy-activity-designer"></a>Usar el diseñador de actividad Legacy
En este tema se describe cómo usar el diseñador de actividad en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el diseñador heredado cuando tenga como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 El diseñador de actividades le permite crear sus propias actividades personalizadas.

## <a name="creating-a-custom-activity"></a>Crear una actividad personalizada
 Siga estos pasos para crear una actividad personalizada con el diseñador de actividades:

1. On the **Project** menu, click **Add Activity**.

2. Select the **Activity** or **Activity (with code separation)** template.

   1. Use the **Activity** template to create an activity with the activity definition and the user code in same code file.

   2. Use the **Activity (with code separation)** template to create an activity with the activity definition expressed as workflow markup and the user code in a separate code file.

3. Type an activity name or keep the default name, and then click **Add**.

   You can also create a set of custom activities by creating a new project of type **Workflow Activity Library**. For more information about this project type, see [How to: Create a Workflow Activity Library (Legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Configurar una actividad
 Aunque el diseñador de actividades esté activo, puede utilizar el explorador de propiedades para configurar las propiedades enumeradas en la siguiente tabla.

|Propiedad.|Comentarios|
|--------------|--------------|
|**Nombre**|Nombre de la actividad.|
|**Base Class**|Clase base de la que deriva la actividad. The default base class is [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). In the **Properties** window, click the **Base Class** ellipses **[…]** to select another base class in the [Browse and Select a .NET Type Dialog Box (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Descripción**|Descripción de la actividad definida por el usuario.|
|**Habilitado**|Set to **True** by default to enable activity execution and validation. Set to **False** to disable activity execution and validation. For information about activity execution and validation, see [Developing Workflow Activities](https://go.microsoft.com/fwlink?LinkID=65024).|

## <a name="adding-child-activities"></a>Agregar actividades secundarias
 Puede arrastrar actividades secundarias del cuadro de herramientas hasta la actividad que esté diseñando. Puede configurar cada una de las actividades secundarias con el explorador de propiedades.

## <a name="see-also"></a>Vea también
 [Developing Workflow Activities](https://go.microsoft.com/fwlink?LinkID=65024) [Creating Custom Activities](https://go.microsoft.com/fwlink?LinkID=65021) [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md) [Custom Activities Samples](https://go.microsoft.com/fwlink?LinkID=65022) [How to: Create a Workflow Activity Library (Legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md) [Using the Legacy Workflow Designer](../workflow-designer/using-the-legacy-workflow-designer.md)