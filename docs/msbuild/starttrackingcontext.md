---
title: StartTrackingContext | Microsoft Docs
description: Obtenga información sobre los parámetros, los requisitos y el valor devuelto para StartTrackingContext de MSBuild, que inicia un contexto de seguimiento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 15121f050fd5af9a5cb36ce15ffc2161076df06d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929126"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

Inicia un contexto de seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parámetros

[in] `intermediateDirectory`

 El directorio en el que almacenar el registro de seguimiento.

[in] `taskName`

 Identifica el contexto de seguimiento. Este nombre se usa para crear el nombre del archivo de registro.

## <a name="return-value"></a>Valor devuelto

 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el contexto de seguimiento se ha creado.

## <a name="requirements"></a>Requisitos

 **Encabezado:** *FileTracker.h*
