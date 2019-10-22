---
title: Finalización de código de IntelliSense para tipos no importados
description: Cómo usar la finalización de código de IntelliSense para los tipos que aún no se han importado con una directiva `using`.
ms.date: 06/20/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f313cfa8520e4c13b310be0f9223466c529ca18f
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2019
ms.locfileid: "67312922"
---
# <a name="intellisense-completion-for-unimported-types"></a>Finalización de código de IntelliSense para tipos no importados

Esta refactorización se aplica a lo siguiente:

- C#

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
