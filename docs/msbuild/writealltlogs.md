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
ms.openlocfilehash: 7eadb30ee25b1182be5deb12feebd5ef280ebf4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630683"
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