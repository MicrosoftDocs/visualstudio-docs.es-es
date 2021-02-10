---
title: CvLeaveSpan (función) | Microsoft Docs
description: Consulte la información de referencia de la función del SDK CvLeaveSpan del visualizador de simultaneidad (biblioteca de C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: da049fc5cc96e9eaa6830159db8c60f9469e2ac4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948262"
---
# <a name="cvleavespan-function"></a>Función CvLeaveSpan
Marca el final del intervalo.

## <a name="syntax"></a>Sintaxis

```C
HRESULT CvLeaveSpan(
   _In_ PCV_SPAN pSpan
);
```

#### <a name="parameters"></a>Parámetros
 `pSpan` Objeto de intervalo devuelto por una llamada anterior a CvEnterSpan*. No puede ser NULL.

## <a name="return-value"></a>Valor devuelto
 S_OK cuando el mensaje se ha escrito correctamente. Código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkers.h*

## <a name="see-also"></a>Consulte también
- [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)