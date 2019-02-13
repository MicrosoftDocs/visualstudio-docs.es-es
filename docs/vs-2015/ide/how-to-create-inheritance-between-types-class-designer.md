---
title: Procedimiento Crear la herencia entre tipos (Diseñador de clases) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d1c5b5d75dedf45988291459ed55b31bf80fc583
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760243"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Cómo: Crear la herencia entre tipos (Diseñador de clases) 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Herencia](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)   
 [Fundamentos de la herencia](http://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5)   
 [Cómo: Ver la herencia entre tipos (Diseñador de clases)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Clases de Visual C++ en el Diseñador de clases](../ide/visual-cpp-classes-in-class-designer.md)
