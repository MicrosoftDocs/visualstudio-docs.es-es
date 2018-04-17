---
title: Los objetos que se va a agregar al diseñador usan una conexión de datos diferentes de que está usando el diseñador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c738a9beb0f2807a186a7c8b8e3f7138c82c9bfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Los objetos que va a agregar al diseñador usan una conexión de datos diferente a la que está usando el diseñador
Los objetos que va a agregar al diseñador usan una conexión de datos diferente a la que está usando el diseñador. ¿Desea reemplazar la conexión que usa el diseñador?  
  
 Cuando se agregan elementos a la [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), todos los elementos usan una conexión de datos compartido. (La superficie de diseño representa la clase <xref:System.Data.Linq.DataContext>, que usa una sola conexión para todos los objetos en la superficie.) Si agrega al diseñador un objeto que usa una conexión de datos distinta de la conexión de datos que usa actualmente el diseñador, aparece este mensaje. Para resolver este error, puede optar por mantener la conexión existente. Si elige esta opción, no se agregará el objeto seleccionado. Asimismo, puede optar por agregar el objeto y restablecer el <xref:System.Data.Linq.DataContext> conexión a la nueva conexión.  
  
> [!NOTE]
>  Si hace clic en **Sí**, clases de entidad todos en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] se asignan a la nueva conexión.  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Para reemplazar la conexión existente con la conexión que usa el objeto seleccionado  
  
-   Haga clic en **Sí**.  
  
     El objeto seleccionado se agrega al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] y DataContext.Connection se establece en la nueva conexión.  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Para continuar usando la conexión existente y cancelar la adición del objeto seleccionado  
  
-   Haga clic en **No**.  
  
     Se cancela la acción. DataContext.Connection se mantiene establecido en la conexión existente.  
  
## <a name="see-also"></a>Vea también
[Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL de las herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
 