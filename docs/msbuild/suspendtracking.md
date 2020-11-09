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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 164e1a11c7d107bf1d98419d77fdc50ed353f93b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048094"
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