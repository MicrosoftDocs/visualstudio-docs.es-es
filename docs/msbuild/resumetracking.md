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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd6722ca0b930d66a386732dac466a8e4fe36976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937919"
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