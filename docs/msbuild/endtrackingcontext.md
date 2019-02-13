---
title: EndTrackingContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f380b57b95cfc0601984794bf02ad4ed145bac5
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853344"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
Finaliza el contexto de seguimiento actual.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Valor devuelto
Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el contexto de seguimiento ha finalizado.

## <a name="requirements"></a>Requisitos
**Encabezado**: *FileTracker.h*

## <a name="see-also"></a>Vea también
[StartTrackingContext](../msbuild/starttrackingcontext.md)
