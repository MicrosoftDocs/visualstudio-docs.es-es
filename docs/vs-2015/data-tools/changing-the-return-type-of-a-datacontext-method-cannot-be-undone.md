---
title: Cambiar el tipo de valor devuelto de un método DataContext no se puede deshacer | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a53bfc66c379be0d6d90d03314f84eef89bd98a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49233823"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>El cambio del tipo devuelto de un método DataContext no se puede deshacer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El cambio del tipo devuelto de un método DataContext no se puede deshacer. Para volver al tipo generado automáticamente, debe arrastrar de nuevo el elemento desde el Explorador de servidores/Explorador de bases de datos hasta Object Relational Designer. ¿Está seguro de que desea cambiar el tipo devuelto?  
  
 El tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> difiere según la ubicación donde se coloque el elemento en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> que tiene el tipo de valor devuelto de la clase de entidad. Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente. Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método, selecciónelo y haga clic en el **Return Type** propiedad en el **propiedades** ventana.  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>Para cambiar el tipo de valor devuelto de un método de DataContext  
  
-   Haga clic en **Sí**.  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Para salir del cuadro de mensaje sin modificar el tipo de valor devuelto  
  
-   Haga clic en **No**.  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Para revertir al tipo de valor devuelto original después de cambiar el tipo de valor devuelto  
  
1.  Seleccione el <xref:System.Data.Linq.DataContext> método en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] y elimínelo.  
  
2.  Busque el elemento en **Server Explorer/Database Explorer** y arrástrelo hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto predeterminado original.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

