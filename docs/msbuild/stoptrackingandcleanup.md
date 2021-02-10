---
title: StopTrackingAndCleanup | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa StopTrackingAndCleanup para detener todo el seguimiento y liberar toda la memoria usada por la sesión de seguimiento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e74e44289e4fd04acf82170584af8645767b63e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905239"
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

 **Encabezado:** *FileTracker.h*

## <a name="see-also"></a>Consulte también

- [StartTrackingContext](../msbuild/starttrackingcontext.md)