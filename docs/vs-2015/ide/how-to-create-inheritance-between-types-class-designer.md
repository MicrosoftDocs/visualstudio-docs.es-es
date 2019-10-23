---
title: Procedimiento Crear herencia entre tipos (Diseñador de clases) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba27b32cc322da2e14cec86b878a7dd42dae0039
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668108"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Procedimiento Crear la herencia entre tipos en el Diseñador de clases
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para crear una relación de herencia entre dos tipos de un diagrama de clases mediante el Diseñador de clases, conecte el tipo base con el tipo o los tipos derivados. Puede haber una relación de herencia entre dos clases, entre una clase y una interfaz o entre dos interfaces.

### <a name="to-create-an-inheritance-between-types"></a>Para crear una herencia entre tipos

1. Desde el proyecto, en el Explorador de soluciones, abra un archivo de diagrama de clases (.cd).

     Si no tiene un diagrama de clases, créelo. Vea [Cómo: Agregar diagramas de clases a proyectos (Diseñador de clases) ](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

2. En el **Cuadro de herramientas**, en **Diseñador de clases**, haga clic en **Herencia**.

3. En el diagrama de clases, dibuje una línea de herencia entre los tipos que desee, desde:

    - Una clase derivada a la clase base

    - Una clase de implementación a la interfaz implementada

    - Una interfaz de extensión a la interfaz extendida

4. Opcionalmente, cuando tenga un tipo derivado de un tipo genérico, haga clic en la línea de herencia. En la ventana **Propiedades**, establezca la propiedad **Argumentos de tipo** para que coincida con el tipo que quiera para el tipo genérico.

    > [!NOTE]
    > Si una clase abstracta principal contiene como mínimo un miembro abstracto, todos los miembros abstractos se implementan como clases de herencia no abstractas.
    >
    >  Aunque puede visualizar los tipos genéricos existentes, no puede crear tipos genéricos nuevos. Tampoco puede cambiar los parámetros de tipo de los tipos genéricos existentes.

## <a name="see-also"></a>Vea también
 Los [conceptos básicos de herencia](https://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5) de [herencia](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea) [How para: Ver la herencia entre tipos (Diseñador de clases) [](../ide/how-to-view-inheritance-between-types-class-designer.md) C++ clases visuales en diseñador de clases](../ide/visual-cpp-classes-in-class-designer.md)
