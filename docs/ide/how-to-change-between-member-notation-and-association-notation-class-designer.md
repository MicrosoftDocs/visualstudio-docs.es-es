---
title: "How to: Change Between Member Notation and Association Notation (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "notation, member"
  - "association notation"
  - "member notation"
  - "notation, association"
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Change Between Member Notation and Association Notation (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En el Diseñador de clases, puede cambiar la manera en que el diagrama de clases representa una relación de asociación entre dos tipos de notación de miembro a notación de asociación, y viceversa.  Los miembros que se muestran como líneas de asociación suelen ofrecer una visión útil de las relaciones existentes entre tipos.  
  
> [!NOTE]
>  Las relaciones de asociación se pueden representar como propiedad o campo de un miembro.  Para cambiar de notación de miembro a notación de asociación, un tipo debe tener un miembro de otro tipo.  Para cambiar de notación de asociación a notación de miembro, los dos tipos deben estar conectados por una línea de asociación.  Para obtener más información, vea [How to: Create Associations Between Types \(Class Designer\)](../ide/how-to-create-associations-between-types-class-designer.md).  Si el proyecto contiene varios diagramas de clases, los cambios realizados en la forma en que un diagrama muestra las relaciones de asociación solo afectan a ese diagrama.  Para cambiar la forma en que otro diagrama muestra las relaciones de asociación, abra o muestre el diagrama y siga estos pasos.  
  
### Para cambiar de notación de miembro a notación de asociación  
  
1.  Desde el nodo del proyecto, en el Explorador de soluciones, abra el archivo de diagrama de clases \(.cd\).  
  
2.  En la forma de tipo del diagrama de clases, haga clic con el botón secundario del mouse en la propiedad o el campo de miembro que representa la asociación y elija **Mostrar como asociación**.  
  
    > [!TIP]
    >  Si no hay ninguna propiedad o campo visible en la forma de tipo, los compartimientos de la forma pueden contraerse.  Para expandir la forma de tipo, haga doble clic en el nombre del compartimiento o haga clic con el botón secundario del mouse en la forma de tipo y elija **Expandir**.  
  
     El miembro desaparece del compartimiento en la forma de tipo y aparece una línea de asociación que conecta ambos tipos.  La línea de asociación incluye una etiqueta con el nombre de la propiedad o campo.  
  
### Para cambiar de notación de asociación a notación de miembro  
  
-   En el diagrama de clases, haga clic con el botón secundario del mouse en la línea de asociación y elija **Mostrar como propiedad** o **Mostrar como campo**, según corresponda.  
  
     La línea de asociación desaparece y la propiedad se muestra en el compartimiento correspondiente dentro de su forma de tipo en el diagrama.  
  
## Vea también  
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [How to: View Inheritance Between Types \(Class Designer\)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Viewing Types and Relationships \(Class Designer\)](../ide/viewing-types-and-relationships-class-designer.md)   
 [How to: Visualize a Collection Association \(Class Designer\)](../ide/how-to-visualize-a-collection-association-class-designer.md)