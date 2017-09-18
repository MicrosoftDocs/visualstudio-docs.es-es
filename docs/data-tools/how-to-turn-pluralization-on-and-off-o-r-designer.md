---
title: "C&#243;mo: Activar y desactivar la pluralizaci&#243;n (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Activar y desactivar la pluralizaci&#243;n (Object Relational Designer)
De forma predeterminada, al arrastrar objetos de base de datos con nombres que terminan en s o es desde el **Explorador de servidores**\/**Explorador de bases de datos** hasta el [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md), los nombres de las clases de entidad generadas cambian de plural a singular.Este cambio se produce para representar con mayor precisión la asignación de la clase de entidad con instancias a un solo registro de datos.Por ejemplo, al agregar una tabla Customers al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se genera una clase de entidad denominada Customer debido a que la clase contendrá los datos de un solo cliente.  
  
> [!NOTE]
>  La pluralización está activada de forma predeterminada solamente en la versión en inglés de Visual Studio.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para activar y desactivar la pluralización  
  
1.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, expanda **Herramientas para bases de datos**.  
  
> [!NOTE]
>  Seleccione **Mostrar todas las configuraciones** si el nodo **Herramientas para bases de datos** no está visible.  
  
1.  Haga clic en **Object Relational Designer**.  
  
2.  Establezca **Pluralización de nombres** en **Habilitado** \= **False** para configurar el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] de forma que no cambie los nombres de clase.  
  
3.  Establezca **Pluralización de nombres** en **Habilitado** \= **True** para aplicar las reglas de pluralización a los nombres de clase de los objetos agregados al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)