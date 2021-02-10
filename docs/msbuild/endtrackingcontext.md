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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90f4c8c4a83a496dba537e74dddfde4ae3f2f21a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877231"
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
