---
description: Esta función obtiene el número de versión de la API del complemento de control de código fuente compatible con el complemento de control de código fuente.
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a71d3374ffd65e0e7b9a7b2e654885d84e370a9d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220604"
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

## <a name="see-also"></a>Consulte también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
