---
title: Finalización de código de IntelliSense para tipos no importados
description: Cómo usar la finalización de código de IntelliSense para los tipos que aún no se han importado con una directiva `using`.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 04ea7c94d3dd24c1a511544adca9bfac3370cd71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094254"
---
# <a name="intellisense-completion-for-unimported-types"></a>Finalización de código de IntelliSense para tipos no importados

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** IntelliSense ofrece la finalización de tipos sin importar.

**Cuándo:** quiere agregar un tipo que ya tiene una dependencia en el proyecto, pero la instrucción de importación aún no se agregó al archivo. 

**Por qué:** no tiene que agregar manualmente la instrucción de importación al archivo.

## <a name="how-to"></a>Procedimiento

1. Una vez que empiece a usar un tipo que tiene una dependencia en el proyecto, IntelliSense proporcionará sugerencias.
2. Presione **Tab**. 

   La instrucción de importación se agregará al archivo.

   ![Finalización de código de IntelliSense para tipos no importados](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
