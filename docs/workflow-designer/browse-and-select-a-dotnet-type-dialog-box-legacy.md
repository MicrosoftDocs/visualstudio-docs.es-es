---
title: "Examinar y seleccionar un cuadro de diálogo de tipo de .NET (heredado) | Documentos de Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 3cdc5d3928cd436d86d529e667f99251e1e7cc95
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Examinar y seleccionar un cuadro de diálogo de tipo .NET (Heredado)
Este tema se describe cómo utilizar el **examinar y seleccionar un tipo .NET** cuadro de diálogo en el Diseñador de flujo de trabajo de Windows heredado. Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 En el **propiedades** ventana, cuando se seleccionan propiedades que toman un tipo de .NET Framework en un ensamblado de referencia, un botón de puntos suspensivos **[...]**  aparece al final del cuadro de texto de la propiedad. Al hacer clic en el **[...]**  abre el **examinar y seleccionar un tipo .NET** cuadro de diálogo. En este cuadro de diálogo, puede escoger un tipo en una vista de árbol de los ensamblados a los que se hace referencia. Por ejemplo, cuando esté utilizando el Diseñador de actividades, en la **propiedades** ventana, haga clic en el **una clase Base** puntos suspensivos **[...]**  para seleccionar otra clase base para una actividad del árbol de ensamblados de referencia.

 La tabla siguiente describen los elementos de interfaz de usuario de la **examinar y seleccionar un tipo .NET** cuadro de diálogo.

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Nombre del tipo:**|Nombre del tipo actualmente seleccionado.|
|**Type**|En el panel izquierdo se muestra una vista de árbol de los Ensamblados a los que se hace referencia. En el panel derecho se muestran los tipos disponibles para la selección del Ensamblado al que se hace referencia seleccionado en el panel izquierdo.|

## <a name="see-also"></a>Vea también

- [Usar el diseñador de actividad Legacy](../workflow-designer/using-the-legacy-activity-designer.md)