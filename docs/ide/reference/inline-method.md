---
title: Método insertado
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones de Visual Studio para refactorizar las declaraciones de métodos insertados y proporcionar una sintaxis más clara.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 80313cf0dd9b828c9602fdf8ebff022342faa0fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852367"
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

    ![Captura de pantalla en la que se muestran el menú Acciones rápidas y refactorizaciones de Visual Studio con la opción "Inline 'CreateWidget()'" (Insertar "CreateWidget[]") seleccionada, y cambios en el código de C#.](media/inline-method-remove-declaration.png)

   Seleccione **Inline and keep `<QualifiedMethodName>`** para conservar la declaración del método original: .

    ![Captura de pantalla en la que se muestran el menú Acciones rápidas y refactorizaciones de Visual Studio con la opción "Inline and keep 'CreateWidget()'" (Insertar y mantener "CreateWidget[]") seleccionada, y cambios en el código de C#.](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
