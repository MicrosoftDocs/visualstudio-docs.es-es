---
title: WriteAllTLogs | Microsoft Docs
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
ms.openlocfilehash: 7c64f0079a03b730fb700cfbc6320c5dffa05d7a
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579517"
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
 **Encabezado**: *FileTracker.h*

## <a name="see-also"></a>Vea también
- [WriteContextTLogs](../msbuild/writecontexttlogs.md)