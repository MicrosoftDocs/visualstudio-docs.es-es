---
title: WriteAllTLogs | Microsoft Docs
description: Obtenga información sobre la sintaxis, los requisitos y el valor devuelto para WriteAllTLogs, que escribe registros de seguimiento para todos los subprocesos y contextos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 754b34b872ba0f0f677a194194b2ff893e7107e1
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047482"
---
# <a name="writealltlogs"></a>WriteAllTLogs

Escribe registros de seguimiento para todos los subprocesos y contextos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parámetros

[in] `intermediateDirectory`

 El directorio en el que almacenar el registro de seguimiento.

[in] `tlogRootName`

 El nombre raíz del nombre del archivo de registro.

## <a name="return-value"></a>Valor devuelto

 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el contexto de seguimiento se ha creado.

## <a name="requirements"></a>Requisitos

 **Encabezado:** *FileTracker.h*

## <a name="see-also"></a>Consulte también

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)