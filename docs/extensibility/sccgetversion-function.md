---
title: SccGetVersion (función) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e2b3818aaa5097313d9150b365544267768507f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708945"
---
# <a name="sccgetversion-function"></a>SccGetVersion (Función)
Esta función obtiene el número de versión de la API de complemento de Control de código fuente compatibles con el complemento de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 Un `LONG` tipo de datos que contiene el número de versión de la API de complemento de Control de origen compatibles:

|WORD|Descripción|
|----------|-----------------|
|HIWORD|Versión principal|
|LOWORD|Versión secundaria|

## <a name="remarks"></a>Comentarios
 Por ejemplo, si un complemento de control de origen es compatible con la versión 1.3 de la API de complemento de Control de origen, esta función debería devolver 0 x 0103.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)