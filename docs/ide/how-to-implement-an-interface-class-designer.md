---
title: "How to: Implement an Interface (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces [Visual Studio], implementing"
  - "interfaces [Visual Studio]"
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Implement an Interface (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En el Diseñador de clases, puede implementar una interfaz en el diagrama de clases conectándolo a una clase que proporcione código para los métodos de la interfaz.  El Diseñador de clases genera una implementación de la interfaz y muestra la relación entre la interfaz y la clase como una relación de herencia.  Puede implementar una interfaz trazando una línea de herencia entre la interfaz y la clase o arrastrando la interfaz desde la Vista de clases.  
  
> [!TIP]
>  Las interfaces se crean del mismo modo en que se crean otros tipos.  Si la interfaz existe pero no aparece en el diagrama de clases, muéstrela primero.  Para obtener más información, vea [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md) y [How to: View Existing Types \(Class Designer\)](../ide/how-to-view-existing-types-class-designer.md).  
  
### Para implementar una interfaz trazando una línea de herencia  
  
1.  En el diagrama de clases, muestre la interfaz y la clase que implementará la interfaz.  
  
2.  Trace una línea de herencia desde la clase a la interfaz.  
  
     Aparece un círculo conectado a la clase y una etiqueta con el nombre de la interfaz identifica la relación de herencia.  Visual Studio genera código auxiliar para todos los miembros de la interfaz.  
  
 Para obtener más información, vea [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### Para implementar una interfaz en la ventana Vista de clases  
  
1.  En el diagrama de clases, muestre la clase que desee que implemente la interfaz.  
  
2.  Abra la Vista de clases y busque la interfaz.  
  
    > [!TIP]
    >  Si la Vista de clases no está abierta, ábrala desde el menú **Ver**.  Para obtener más información sobre la Vista de clases, vea [Viewing Classes and Their Members](http://msdn.microsoft.com/es-es/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Arrastre el nodo de la interfaz hasta la forma de clase en el diagrama.  
  
     Aparece un círculo conectado a la clase y una etiqueta con el nombre de la interfaz identifica la relación de herencia.  Visual Studio genera código auxiliar para todos los miembros de interfaz; llegado este punto, la interfaz está implementada.  
  
## Vea también  
 [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [How to: View Existing Types \(Class Designer\)](../ide/how-to-view-existing-types-class-designer.md)   
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactoring Classes and Types \(Class Designer\)](../ide/refactoring-classes-and-types-class-designer.md)