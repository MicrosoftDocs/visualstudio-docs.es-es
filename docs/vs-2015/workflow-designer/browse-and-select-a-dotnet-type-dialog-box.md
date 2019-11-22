---
title: Browse and Select a .NET Type Dialog Box | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d8e25ad181202a2c7994c116e2220426ca3d8509
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297614"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Examinar y seleccionar un cuadro de diálogo de tipo .NET
In the **Properties** window, dialog boxes, or designers such as the variable designer, when you select **Browse for Types…** from a list of data types, is the **Browse and Select a .NET Type** dialog box (referred to in an abbreviated form as the “type browser”). En este cuadro de diálogo, puede escoger un tipo en una vista de árbol de ensamblados y proyectos.

 Este cuadro de diálogo se emplea en varios escenarios de usuario, lo cual incluye lo siguiente:

- Cuando se establece el tipo de una variable o argumento.

- Cuando se selecciona un tipo para una actividad genérica.

- Cuando se agrega una instrucción catch en la actividad <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> El explorador de tipo puede mostrar tipos de matrices escalonadas Visual Basic de matriz, pero no tipos de matrices multidimensionales. See [Jagged Arrays](https://go.microsoft.com/fwlink/?LinkId=195226) and [Multidimensional Arrays](https://go.microsoft.com/fwlink/?LinkId=195227) for details.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Seleccionar un tipo de valor y de referencia en el explorador de tipo

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Para seleccionar un tipo de valor y de referencia en el explorador de tipo

1. In the **Type Name** box, enter the name of the type that you want to use.

2. Realice una de las siguientes acciones:

    - Once the name of the type that you want to use appears in the tree in the **Type Name** box, double-click the type to select it.

    - Type enough characters in the **Type Name** box to uniquely identify the type that you want to use and then press enter to select the type

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Para seleccionar un tipo genérico en el explorador de tipo

1. In the **Type Name** box, type in the name of the type that you want to use.

2. Once the name of the type that you want to use appears in the tree in the **Type Name** box, click the type to select it to cause drop-down boxes appear.

     Select the type that you want to use to close the generic from the drop-down boxes, and then click **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Tipos que se muestran en el explorador de tipo
 Los tipos que se muestran en el explorador pueden variar en función de cómo se haya iniciado el explorador de tipo. If the type browser was launched from a workflow project inside of **vs2010**, by default all of the types in the referenced assemblies and referenced projects are shown. If the type browser was launched from outside of a **vs2010** project system (such as in a rehosted workflow application or in a standalone workflow file), then by default the types from all of the assemblies loaded in the AppDomain are shown.

 Los tipos en el explorador de tipo se pueden filtrar por desarrolladores de software del diseñador de actividades. Respecto a una actividad en concreto, es posible que vea únicamente un subconjunto de los tipos. Por ejemplo, en la actividad <xref:System.Activities.Statements.TryCatch>, solo se muestran los tipos derivados de <xref:System.Exception> en el explorador de tipo.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtrar los resultados de la búsqueda en el explorador de tipo
 The list of types in the **Type Name** box gets shorter as you type more characters to find a match. Solo aparecerán en la lista filtrada los tipos cuyo nombre completo o cuyo nombre corto comiencen con la cadena que ha escrito.

 Por ejemplo:

1. Typing **Operation** matches <xref:System.OperationCanceledException> but not <xref:System.InvalidOperationException>. Para buscar coincidencias con <xref:System.InvalidOperationException>, comience a escribir System.I o Invalid.

2. Typing **Generic** matches <xref:System.GenericUriParser> but not types in the <xref:System.Collections.Generic> namespace. Para buscar tipos en el espacio de nombres <xref:System.Collections.Generic>, escriba el nombre completo del espacio de nombres.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Seleccionar un contrato de servicio usando el cuadro de diálogo de explorador de tipo
 Al seleccionar un tipo de contrato de servicio, el explorador de tipo muestra únicamente los tipos que tienen el atributo <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>Vea también
 [Usar los diseñadores de actividad](../workflow-designer/using-the-activity-designers.md)