---
title: Los objetos que va a agregar al diseñador usan una conexión de datos diferente a la que el diseñador está usando actualmente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9ec76446aff930475ea5e3ca0133e11b3798b0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672303"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Los objetos que va a agregar al diseñador usan una conexión de datos diferente a la que está usando el diseñador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los objetos que va a agregar al diseñador usan una conexión de datos diferente a la que está usando el diseñador. ¿Desea reemplazar la conexión que usa el diseñador?

 Al agregar elementos al [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), todos los elementos usan una conexión de datos compartida. (La superficie de diseño representa el <xref:System.Data.Linq.DataContext>, que usa una sola conexión para todos los objetos de la superficie). Si agrega un objeto al diseñador que usa una conexión de datos que difiere de la conexión de datos utilizada actualmente por el diseñador, aparece este mensaje. Para resolver este error, puede optar por mantener la conexión existente. Si elige esta opción, no se agregará el objeto seleccionado. Asimismo, puede optar por agregar el objeto y restablecer la conexión de <xref:System.Data.Linq.DataContext> en la nueva conexión.

> [!NOTE]
> Si hace clic en **sí**, todas las clases de entidad del [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] se asignan a la nueva conexión.

### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Para reemplazar la conexión existente con la conexión que usa el objeto seleccionado

- Haga clic en **Sí**.

     El objeto seleccionado se agrega al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] y DataContext.Connection se establece en la nueva conexión.

### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Para continuar usando la conexión existente y cancelar la adición del objeto seleccionado

- Haga clic en **No**.

     Se cancela la acción. DataContext.Connection se mantiene establecido en la conexión existente.

## <a name="see-also"></a>Vea también
 [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)