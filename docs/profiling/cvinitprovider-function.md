---
title: CvInitProvider (función) | Microsoft Docs
description: Consulte la información de referencia de la función del SDK CvInitProvider del visualizador de simultaneidad (biblioteca de C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f23d3ceadf2ee8d1a0c6b53b395c379caf505179
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941000"
---
# <a name="cvinitprovider-function"></a>Función CvInitProvider
Inicializa el proveedor de marcadores. Se debe llamar antes que cualquier otra función del SDK del visualizador de simultaneidad.

## <a name="syntax"></a>Sintaxis

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parámetros
 `pGuid` Guid del proveedor. No puede ser NULL.

 `ppProvider` Dirección de una variable de salida que almacenará el contexto del proveedor. No puede ser NULL.

## <a name="return-value"></a>Valor devuelto
 S_OK cuando el proveedor se inicializa correctamente, o código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkers.h*

## <a name="see-also"></a>Consulte también
- [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)