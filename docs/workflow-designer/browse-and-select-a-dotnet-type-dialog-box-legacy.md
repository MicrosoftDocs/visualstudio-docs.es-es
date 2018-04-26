---
title: 'Diseñador de flujo de trabajo: Examinar y seleccionar un cuadro de diálogo de tipo de .NET (heredado)'
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 23e311aa8e87fe799bc8ea22a22ffd8e789b3dcd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Examinar y seleccionar un cuadro de diálogo de tipo .NET (Heredado)

Este tema se describe cómo utilizar el **examinar y seleccionar un tipo .NET** cuadro de diálogo en el Diseñador de flujo de trabajo de Windows heredado. Use el Diseñador de flujo de trabajo heredado cuando deba tener como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

 En el **propiedades** ventana, cuando se seleccionan propiedades que toman un tipo de .NET Framework en un ensamblado de referencia, un botón de puntos suspensivos **[...]**  aparece al final del cuadro de texto de la propiedad. Al hacer clic en el **[...]**  abre el **examinar y seleccionar un tipo .NET** cuadro de diálogo. En este cuadro de diálogo, puede escoger un tipo en una vista de árbol de los ensamblados a los que se hace referencia. Por ejemplo, cuando esté utilizando el Diseñador de actividades, en la **propiedades** ventana, haga clic en el **una clase Base** puntos suspensivos **[...]**  para seleccionar otra clase base para una actividad del árbol de ensamblados de referencia.

 La tabla siguiente describen los elementos de interfaz de usuario de la **examinar y seleccionar un tipo .NET** cuadro de diálogo.

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Nombre del tipo:**|Nombre del tipo actualmente seleccionado.|
|**Type**|En el panel izquierdo se muestra una vista de árbol de los Ensamblados a los que se hace referencia. En el panel derecho se muestran los tipos disponibles para la selección del Ensamblado al que se hace referencia seleccionado en el panel izquierdo.|

## <a name="see-also"></a>Vea también

- [Usar el diseñador de actividad Legacy](../workflow-designer/using-the-legacy-activity-designer.md)