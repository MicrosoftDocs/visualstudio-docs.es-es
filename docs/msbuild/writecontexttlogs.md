---
title: WriteContextTLogs | Microsoft Docs
description: Obtenga información sobre la sintaxis, los requisitos y el valor devuelto para WriteContextTLogs, que escribe archivos de registro para el contexto actual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b44777f41c4fac3d36cb79222d48a93c5c1cf0b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888009"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs

Escribe archivos de registro para el contexto actual.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
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

- [WriteAllTLogs](../msbuild/writealltlogs.md)