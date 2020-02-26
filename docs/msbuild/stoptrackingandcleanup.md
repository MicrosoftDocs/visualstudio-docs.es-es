---
title: StopTrackingAndCleanup | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a80fcde7aeab601791c033bd21effce175b2cb9
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579565"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Detiene todo el seguimiento y libera la memoria que ha usado la sesión de seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Valor devuelto
 Devuelve un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el seguimiento se ha detenido.

## <a name="requirements"></a>Requisitos
 **Encabezado**: *FileTracker.h*

## <a name="see-also"></a>Vea también
- [StartTrackingContext](../msbuild/starttrackingcontext.md)