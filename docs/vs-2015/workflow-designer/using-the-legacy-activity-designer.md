---
title: Usar el diseñador de actividad heredado | Microsoft Docs
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
ms.openlocfilehash: cd8d18d95fabd858354c625d2c9b32459efc7193
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846153"
---
# <a name="using-the-legacy-activity-designer"></a>Usar el diseñador de actividad Legacy
En este tema se describe cómo usar el diseñador de actividad en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el diseñador heredado cuando tenga como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 El diseñador de actividades le permite crear sus propias actividades personalizadas.

## <a name="creating-a-custom-activity"></a>Crear una actividad personalizada
 Siga estos pasos para crear una actividad personalizada con el diseñador de actividades:

1. En el menú **proyecto** , haga clic en **Agregar actividad**.

2. Seleccione la plantilla **actividad** o **actividad (con separación de código)** .

   1. Use la plantilla de **actividad** para crear una actividad con la definición de actividad y el código de usuario en el mismo archivo de código.

   2. Use la plantilla **actividad (con separación de código)** para crear una actividad con la definición de actividad expresada como marcado de flujo de trabajo y el código de usuario en un archivo de código independiente.

3. Escriba un nombre de actividad o mantenga el nombre predeterminado y, a continuación, haga clic en **Agregar**.

   También puede crear un conjunto de actividades personalizadas creando un nuevo proyecto de tipo biblioteca de **actividades de flujo de trabajo**. Para obtener más información acerca de este tipo de proyecto, consulte [Cómo: crear una biblioteca de actividades de flujo de trabajo (heredado)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Configurar una actividad
 Aunque el diseñador de actividades esté activo, puede utilizar el explorador de propiedades para configurar las propiedades enumeradas en la siguiente tabla.

|La propiedad|Comentarios|
|--------------|--------------|
|**Name**|Nombre de la actividad.|
|**Clase base**|Clase base de la que deriva la actividad. La clase base predeterminada es [SequenceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequenceactivity.aspx). En la ventana **propiedades** , haga clic en los puntos suspensivos **[...]** de la **clase base** para seleccionar otra clase base en el [cuadro de diálogo examinar y seleccionar un tipo .net (heredado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Descripción**|Descripción de la actividad definida por el usuario.|
|**Habilitado**|Se establece en **true** de forma predeterminada para habilitar la ejecución y validación de la actividad. Establézcalo en **false** para deshabilitar la ejecución y validación de la actividad. Para obtener información sobre la ejecución y validación de actividades, vea [desarrollar actividades de flujo de trabajo](https://msdn2.microsoft.com/library/ms734413.aspx).|

## <a name="adding-child-activities"></a>Agregar actividades secundarias
 Puede arrastrar actividades secundarias del cuadro de herramientas hasta la actividad que esté diseñando. Puede configurar cada una de las actividades secundarias con el explorador de propiedades.

## <a name="see-also"></a>Vea también
 [Desarrollo de actividades de flujo de trabajo](https://msdn2.microsoft.com/library/ms734413.aspx) [creación](https://msdn2.microsoft.com/library/bb675228.aspx) de actividades personalizadas actividades de [flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md) actividades [personalizadas ejemplos](https://msdn2.microsoft.com/library/bb472471.aspx) [Cómo: crear una biblioteca de actividades de flujo de trabajo (heredada)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md) [mediante el diseñador de flujo de trabajo heredado](../workflow-designer/using-the-legacy-workflow-designer.md)
