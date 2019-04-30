---
title: 'Error: No se admite la depuración en modo mixto para los procesos IA64 | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c4414651249aa7622e7f7be59e6150a4925f1b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850864"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Error: No se admite la depuración en modo mixto de procesos IA64
El depurador [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no permite depurar código nativo y administrado mixto en un proceso basado en Itanium.

### <a name="to-correct-this-error"></a>Para corregir este error

- Compile una versión de 32 bits de su aplicación para la depuración.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)