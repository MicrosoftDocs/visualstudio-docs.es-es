---
title: "Cómo: ampliar código generado por el diseñador O-R | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: e5b38288cc8d0d58e18e4aea3de2b80470783ea6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Cómo: Ampliar código generado por Object Relational Designer
El código generado por el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] se vuelve a generar cuando se realizan cambios en las clases de entidad y en otros objetos de la superficie del diseñador. Debido a esta regeneración del código, cualquier código que se agregue al código generado se suele sobrescribir cuando el diseñador vuelve a generar el código. El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] permite generar archivos de clases parciales en los que se puede agregar código que no se sobrescribirá. Un ejemplo de cómo agregar código propio al código generado por el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sería agregar validación de datos a las clases (de entidad) de LINQ to SQL. Para obtener información, consulte [Cómo: agregar validación a clases de entidad](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>Agregar código a una clase de entidad  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Para crear una clase parcial y agregar código a una clase de entidad  
  
1.  Abra o cree un nuevo archivo LINQ to SQL Classes (**.dbml** archivo) en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Haga doble clic en el **.dbml** en el archivo **el Explorador de soluciones**/**Database Explorer**.)  
  
2.  En el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], haga clic en la clase para la que desea agregar la validación y, a continuación, haga clic en **ver código**.  
  
     El Editor de código se abre con una clase parcial para la clase de entidad seleccionada.  
  
3.  Agregue código a la declaración de clase parcial para la clase de entidad.  
  
## <a name="adding-code-to-a-datacontext"></a>Agregar código a una clase DataContext  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Para crear una clase parcial y agregar código a una clase DataContext  
  
1.  Abra o cree un nuevo archivo LINQ to SQL Classes (**.dbml** archivo) en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Haga doble clic en el **.dbml** en el archivo **el Explorador de soluciones**/**Database Explorer**.)  
  
2.  En el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], haga clic en un área vacía en el diseñador y, a continuación, haga clic en **ver código**.  
  
     El Editor de código se abre con una clase parcial de DataContext.  
  
3.  Agregue código a la declaración de clase parcial para DataContext.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 