---
title: ResumeTracking | Microsoft Docs
description: Obtenga información sobre la sintaxis, los requisitos y el valor devuelto para MSBuild ResumeTracking, que reanuda el seguimiento en el contexto actual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9af7c90342638fb0c154e7de21fa111d560905d0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048428"
---
# <a name="resumetracking"></a>ResumeTracking

Reanuda el seguimiento en el contexto actual.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Valor devuelto

 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el seguimiento se ha reanudado. **E_FAIL** se devuelve si el seguimiento no puede reanudarse porque no está disponible el contexto.

## <a name="requirements"></a>Requisitos

 **Encabezado:** *FileTracker.h*

## <a name="see-also"></a>Consulte también

- [SuspendTracking](../msbuild/suspendtracking.md)