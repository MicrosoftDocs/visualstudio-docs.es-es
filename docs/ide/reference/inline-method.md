---
title: Método insertado
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0cc619ea61a7fd4d7f4bc542b946e298933a8f73
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403569"
---
# <a name="inline-method"></a>Método insertado

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Refactorización de un método insertado. 

**Cuándo:** Desea reemplazar las utilizaciones de un método estático, de instancia y de extensión dentro de un cuerpo de instrucción único con una opción para quitar la declaración de método original.

**Por qué:**  Esta refactorización proporcionará una sintaxis más clara.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor de inserción en la utilización del método.

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

3. Seleccione una de las opciones siguientes: 
    
   Seleccione **Inline `<QualifiedMethodName>`** para quitar la declaración del método insertado: .

    ![Conversión de la clase en abstracta](media/inline-method-remove-declaration.png)

   Seleccione **Inline and keep `<QualifiedMethodName>`** para conservar la declaración del método original: .

    ![Conversión de la clase en abstracta](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
