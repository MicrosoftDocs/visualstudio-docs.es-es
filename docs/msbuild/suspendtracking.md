---
title: SuspendTracking | Microsoft Docs
description: Obtenga información sobre la sintaxis, los requisitos y el valor devuelto para SuspendTracking de MSBuild, que suspende el seguimiento en el contexto actual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e8be768bc48c1815fc00069640e5bf3f4370f434
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945284"
---
# <a name="suspendtracking"></a>SuspendTracking

Suspende el seguimiento en el contexto actual.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Valor devuelto

 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el seguimiento se ha suspendido.

## <a name="requirements"></a>Requisitos

 **Encabezado:** *FileTracker.h*

## <a name="see-also"></a>Consulte también

- [ResumeTracking](../msbuild/resumetracking.md)