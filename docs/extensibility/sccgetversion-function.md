---
title: Función SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a563a7d1d65dc4c6564abd4e337242eea1aa9924
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700673"
---
# <a name="sccgetversion-function"></a>SccGetVersion (Función)
Esta función obtiene el número de versión de la API del complemento de control de código fuente compatible con el complemento de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 Un `LONG` tipo de datos que contiene el número de versión de la API del complemento de control de código fuente compatible:

|WORD|Descripción|
|----------|-----------------|
|HIWORD|Versión principal|
|LOWORD|Versión secundaria|

## <a name="remarks"></a>Observaciones
 Por ejemplo, si un complemento de control de código fuente admite la versión 1,3 de la API del complemento de control de código fuente, esta función devolverá 0x0103.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
