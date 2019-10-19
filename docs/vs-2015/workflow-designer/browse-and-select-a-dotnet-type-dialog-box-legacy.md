---
title: Examinar y seleccionar un cuadro de diálogo de tipo .NET (heredado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e5045a62d0a654af968d50e0c309bcf8104b5cc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668988"
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Examinar y seleccionar un cuadro de diálogo de tipo .NET (Heredado)
En este tema se describe cómo usar el cuadro de diálogo **examinar y seleccionar un tipo .net** en el [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 En la ventana **propiedades** , cuando se seleccionan las propiedades que toman un .NET Framework tipo de un ensamblado al que se hace referencia, aparecen puntos suspensivos **[...]** al final del cuadro de texto de la propiedad. Al hacer clic en **[...]** , se abre el cuadro de diálogo **examinar y seleccionar un tipo .net** . En este cuadro de diálogo, puede escoger un tipo en una vista de árbol de los ensamblados a los que se hace referencia. Por ejemplo, si usa el diseñador de actividad, en la ventana **propiedades** , haga clic en los puntos suspensivos **[...]** de la **clase base** para seleccionar otra clase base para una actividad del árbol de ensamblados al que se hace referencia.

 En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **examinar y seleccionar un tipo .net** .

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Nombre de tipo:**|Nombre del tipo actualmente seleccionado.|
|**ype**|En el panel izquierdo se muestra una vista de árbol de los Ensamblados a los que se hace referencia. En el panel derecho se muestran los tipos disponibles para la selección del Ensamblado al que se hace referencia seleccionado en el panel izquierdo.|

## <a name="see-also"></a>Vea también
 [Usar el diseñador de actividad Legacy](../workflow-designer/using-the-legacy-activity-designer.md)