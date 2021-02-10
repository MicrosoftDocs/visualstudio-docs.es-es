---
title: Finalización de IntelliSense para métodos de extensión
description: Cómo usar la finalización de IntelliSense para los tipos y los métodos de extensión que aún no se han importado con una directiva `using`.
ms.custom: SEO-VS-2020
ms.date: 07/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2b73b4d73c36215b70b7551298492e39b69e179f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852341"
---
# <a name="intellisense-completion-for-unimported-types-and-extension-methods"></a>Finalización de IntelliSense para tipos y métodos de extensión no importados

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** IntelliSense ofrece finalización para tipos y métodos de extensión no importados.

**Cuándo:** quiere usar un tipo o un método de extensión que ya tiene una dependencia en el proyecto, pero la instrucción using aún no se ha agregado al archivo.

**Por qué:** no tiene que agregar manualmente la instrucción using al archivo.

## <a name="how-to"></a>Procedimiento

1. Una vez que empiece a escribir el nombre de un tipo o método de extensión que tiene una dependencia en el proyecto, IntelliSense proporcionará sugerencias. Los elementos de los espacios de nombres no importados mostrarán como sufijo el espacio de nombres contenedor.

   > [!TIP]
   > Puede mostrar u ocultar elementos de espacios de nombres no importados a petición, mediante el **botón de expansión (Alt+A)** que aparece en la parte inferior izquierda de la lista de finalización. Para cambiar el comportamiento predeterminado, vaya a **Herramientas** > **Opciones** > **Editor de texto** > **C#**  / **Basic** > **IntelliSense** y busque **Show items from unimported namespaces** (Mostrar elementos de espacios de nombres no importados).

2. Seleccione y confirme un elemento no importado.

   La instrucción using se agregará automáticamente al archivo.

   ![Finalización de código de IntelliSense para tipos no importados](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Consulte también

- [IntelliSense](../using-intellisense.md)
- [Refactorización](../refactoring-in-visual-studio.md)
