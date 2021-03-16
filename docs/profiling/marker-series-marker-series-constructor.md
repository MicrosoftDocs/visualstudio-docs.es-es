---
description: Inicializa una nueva instancia de la clase marker_series.
title: marker_series::marker_series (Constructor) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency, diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 88d82c78bc6126f6b3d96b77b39c729c4f452a28
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223984"
---
# <a name="marker_seriesmarker_series-constructor"></a>Constructor marker_series::marker_series
Inicializa una nueva instancia de la clase `marker_series`.

## <a name="syntax"></a>Sintaxis

```cpp
marker_series();
marker_series(
   _In_ LPCTSTR _SeriesName
);
marker_series(
   _In_ const GUID* _ProviderGuid
);
marker_series(
   _In_ const GUID* _ProviderGuid,
   _In_ LPCTSTR _SeriesName
);
```

#### <a name="parameters"></a>Parámetros
 `_SeriesName` Nombre de la serie que se va a crear.

 `_ProviderGuid` El GUID del proveedor de la serie.

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkersobj.h*

 **Espacio de nombres:** Concurrency::diagnostic

## <a name="see-also"></a>Consulte también
- [Clase marker_series](../profiling/marker-series-class.md)
