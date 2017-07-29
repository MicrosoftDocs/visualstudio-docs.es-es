---
title: "Cómo: Crear la herencia entre tipos (Diseñador de clases) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 30
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: bd4969c26d1cc0043945189bd4da3acbf5792107
ms.contentlocale: es-es
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Cómo: Crear la herencia entre tipos (Diseñador de clases)
Para crear una relación de herencia entre dos tipos de un diagrama de clases mediante el Diseñador de clases, conecte el tipo base con el tipo o los tipos derivados. Puede haber una relación de herencia entre dos clases, entre una clase y una interfaz o entre dos interfaces.  
  
### <a name="to-create-an-inheritance-between-types"></a>Para crear una herencia entre tipos  
  
1.  Desde el proyecto, en el Explorador de soluciones, abra un archivo de diagrama de clases (.cd).  
  
     Si no tiene un diagrama de clases, créelo. Vea [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2.  En el **Cuadro de herramientas**, en **Diseñador de clases**, haga clic en **Herencia**.  
  
3.  En el diagrama de clases, dibuje una línea de herencia entre los tipos que desee, desde:  
  
    -   Una clase derivada a la clase base  
  
    -   Una clase de implementación a la interfaz implementada  
  
    -   Una interfaz de extensión a la interfaz extendida  
  
4.  Opcionalmente, cuando tenga un tipo derivado de un tipo genérico, haga clic en la línea de herencia. En la ventana **Propiedades**, establezca la propiedad **Argumentos de tipo** para que coincida con el tipo que quiera para el tipo genérico.  
  
    > [!NOTE]
    >  Si una clase abstracta principal contiene como mínimo un miembro abstracto, todos los miembros abstractos se implementan como clases de herencia no abstractas.  
    >   
    >  Aunque puede visualizar los tipos genéricos existentes, no puede crear tipos genéricos nuevos. Tampoco puede cambiar los parámetros de tipo de los tipos genéricos existentes.  
  
## <a name="see-also"></a>Vea también  
 [Herencia](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Cómo: Ver la herencia entre tipos (Diseñador de clases)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Clases de Visual C++ en el Diseñador de clases](../ide/visual-cpp-classes-in-class-designer.md)
