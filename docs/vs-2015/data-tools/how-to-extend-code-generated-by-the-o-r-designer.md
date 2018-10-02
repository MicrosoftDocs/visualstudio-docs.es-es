---
title: 'Cómo: ampliar código generado por el Object Relational Designer | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8fe770e52a1557d577ef2536177321deb04c0128
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577798"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Cómo: Ampliar código generado por Object Relational Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: ampliar código generado por el Object Relational Designer](https://docs.microsoft.com/visualstudio/data-tools/how-to-extend-code-generated-by-the-o-r-designer).  
  
  
El código generado por el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] se vuelve a generar cuando se realizan cambios en las clases de entidad y en otros objetos de la superficie del diseñador. Debido a esta regeneración del código, cualquier código que se agregue al código generado se suele sobrescribir cuando el diseñador vuelve a generar el código. El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] permite generar archivos de clases parciales en los que se puede agregar código que no se sobrescribirá. Un ejemplo de cómo agregar código propio al código generado por el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] sería agregar validación de datos a las clases (de entidad) de LINQ to SQL. Para obtener información, consulte [Cómo: agregar validación a clases de entidad](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>Agregar código a una clase de entidad  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Para crear una clase parcial y agregar código a una clase de entidad  
  
1.  Abra o cree un nuevo archivo LINQ to SQL Classes (**.dbml** archivo) en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Haga doble clic en el **.dbml** archivo **el Explorador de soluciones**/**Database Explorer**.)  
  
2.  En el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], haga clic en la clase para el que desea agregar la validación y, a continuación, haga clic en **ver código**.  
  
     El Editor de código se abre con una clase parcial para la clase de entidad seleccionada.  
  
3.  Agregue código a la declaración de clase parcial para la clase de entidad.  
  
## <a name="adding-code-to-a-datacontext"></a>Agregar código a una clase DataContext  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Para crear una clase parcial y agregar código a una clase DataContext  
  
1.  Abra o cree un nuevo archivo LINQ to SQL Classes (**.dbml** archivo) en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Haga doble clic en el **.dbml** archivo **el Explorador de soluciones**/**Database Explorer**.)  
  
2.  En el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], haga clic en un área vacía en el diseñador y, a continuación, haga clic en **ver código**.  
  
     El Editor de código se abre con una clase parcial de DataContext.  
  
3.  Agregue código a la declaración de clase parcial para DataContext.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Tutorial: Agregar validación a clases de entidad](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)

