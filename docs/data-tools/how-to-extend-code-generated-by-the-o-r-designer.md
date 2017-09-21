---
title: "C&#243;mo: Extender c&#243;digo generado por Object Relational Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Extender c&#243;digo generado por Object Relational Designer
El código generado por el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] se vuelve a generar cuando se realizan cambios en las clases de entidad y en otros objetos de la superficie del diseñador.Debido a esta regeneración del código, cualquier código que se agregue al código generado se suele sobrescribir cuando el diseñador vuelve a generar el código.El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] permite generar archivos de clases parciales en los que se puede agregar código que no se sobrescribirá.Un ejemplo de cómo agregar código propio al código generado por el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sería agregar validación de datos a las clases \(de entidad\) de LINQ to SQL.Para obtener más información, vea [Cómo: Agregar validación a clases de entidad](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Agregar código a una clase de entidad  
  
#### Para crear una clase parcial y agregar código a una clase de entidad  
  
1.  Abra o cree un nuevo archivo de clases de LINQ to SQL \(archivo **.dbml**\) en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].\(Haga doble clic en el archivo **.dbml** en el **Explorador de soluciones**\/**Explorador de bases de datos**.\)  
  
2.  En el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], haga clic con el botón secundario del mouse en la clase para la que desee agregar validación y, a continuación, haga clic en **Ver código**.  
  
     El Editor de código se abre con una clase parcial para la clase de entidad seleccionada.  
  
3.  Agregue código a la declaración de clase parcial para la clase de entidad.  
  
## Agregar código a una clase DataContext  
  
#### Para crear una clase parcial y agregar código a una clase DataContext  
  
1.  Abra o cree un nuevo archivo de clases de LINQ to SQL \(archivo **.dbml**\) en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].\(Haga doble clic en el archivo **.dbml** en el **Explorador de soluciones**\/**Explorador de bases de datos**.\)  
  
2.  En el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], haga clic con el botón secundario del mouse en un área vacía del diseñador y, a continuación, haga clic en **Ver código**.  
  
     El Editor de código se abre con una clase parcial de DataContext.  
  
3.  Agregue código a la declaración de clase parcial para DataContext.  
  
## Vea también  
 [Información general sobre Object Relational Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Tutorial: Agregar validación a clases de entidad](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md)