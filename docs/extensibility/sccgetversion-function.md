---
description: Esta función obtiene el número de versión de la API del complemento de control de código fuente compatible con el complemento de control de código fuente.
title: SccGetVersion Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f49d33ebe70390a364d0ae8336e7f69549b6876f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901089"
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
 Tipo de datos que contiene el número de versión de la API de complemento `LONG` de control de código fuente compatible:

|WORD|Descripción|
|----------|-----------------|
|HIWORD|Versión principal|
|LOWORD|Versión secundaria|

## <a name="remarks"></a>Observaciones
 Por ejemplo, si un complemento de control de código fuente admite la versión 1.3 de la API del complemento de control de código fuente, esta función devolvería 0x0103.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
