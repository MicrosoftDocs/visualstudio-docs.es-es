---
title: "Acercar declaración a referencia - refactorización (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.openlocfilehash: f784ac9fec1dce1f21ba4b9f1f0e83b4b7deb001
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/29/2017
---
# <a name="move-declaration-near-reference-in-c"></a>Mueva la declaración cerca de referencia en C# #
**¿Qué:** permite mover hacia las declaraciones de variable para su uso.

**Cuándo:** tienen declaraciones de variables que pueden estar en un ámbito más restringido.

**Por este motivo:** , puede dejarlo tal y como es, pero que pueden causar problemas de legibilidad u ocultar información. Se trata de una oportunidad de refactorización para mejorar la legibilidad.

**Cómo:**

1. Coloque el cursor en la declaración de variable.

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **Acercar declaración a referencia** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **Acercar declaración a referencia** desde la ventana emergente de ventana de vista previa.

1. Cuando esté satisfecho con el cambio, presione **ENTRAR** o haga clic en la solución en el menú y los cambios se confirmarán.

Ejemplo:
```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Vea también  
[Refactorización (C#)](../refactoring-csharp.md)  
[Vista previa de cambios](../../ide/preview-changes.md)