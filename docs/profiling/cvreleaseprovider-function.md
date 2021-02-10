---
title: CvReleaseProvider (función) | Microsoft Docs
description: Consulte la información de referencia de la función del SDK CvReleaseProvider del visualizador de simultaneidad (biblioteca de C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae363f1909f169d2d5dc4004a79cfe3c2919bdf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948236"
---
# <a name="cvreleaseprovider-function"></a>Función CvReleaseProvider
Libera el proveedor de marcadores. Liberar el proveedor de marcadores no afectará a la serie de marcadores de este proveedor creada anteriormente. La serie de marcadores debe liberarse por separado mediante la llamada de CvReleaseMarkerSeries. Si no se puede liberar el proveedor, se produce una pérdida de memoria.

## <a name="syntax"></a>Sintaxis

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>Parámetros
 `pProvider` Contexto de proveedor. No puede ser NULL.

## <a name="return-value"></a>Valor devuelto
 S_OK cuando el proveedor se libera correctamente, o código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkers.h*

## <a name="see-also"></a>Consulte también
- [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)