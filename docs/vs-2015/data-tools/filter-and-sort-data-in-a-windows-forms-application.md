---
title: Filtrar y ordenar datos en una aplicación Windows Forms | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24c623efc141ff84c2585f967596271d1efbc502
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671643"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrar y ordenar los datos en una aplicación Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los datos se filtran estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.Filter%2A> en una expresión de cadena que devuelve los registros deseados.

 Puede ordenar los datos estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.Sort%2A> en el nombre de columna por la que desea ordenar; anexe `DESC` para realizar la ordenación en sentido descendente, o bien, `ASC` para hacerlo en sentido ascendente.

> [!NOTE]
> Si la aplicación no usa <xref:System.Windows.Forms.BindingSource> componentes, puede filtrar y ordenar los datos mediante <xref:System.Data.DataView> objetos. Para obtener más información, vea las [vistas](https://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b)de datos.

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Para filtrar los datos mediante un componente BindingSource

- Establezca la propiedad <xref:System.Windows.Forms.BindingSource.Filter%2A> en la expresión que desea devolver. Por ejemplo, el código siguiente devuelve los clientes cuyo valor de `CompanyName` empieza por "B":

     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Para ordenar los datos mediante un componente BindingSource

- Establezca la propiedad <xref:System.Windows.Forms.BindingSource.Sort%2A> en la columna por la que desea ordenar. Por ejemplo, el código siguiente ordena los clientes por la columna `CompanyName` en orden descendente:

     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]

## <a name="see-also"></a>Consulte también
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
