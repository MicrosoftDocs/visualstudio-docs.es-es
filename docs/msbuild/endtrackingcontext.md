---
title: EndTrackingContext | Microsoft Docs
description: Conozca la sintaxis, el valor devuelto y los requisitos para usar EndTrackingContext de MSBuild para finalizar el contexto de seguimiento actual.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da1ef921106732a7787f68a979bc88f3ac012b6d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436669"
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

**Encabezado:** *FileTracker.h*

## <a name="see-also"></a>Consulte también

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
