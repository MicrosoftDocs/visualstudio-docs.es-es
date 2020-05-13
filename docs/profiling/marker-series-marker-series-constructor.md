---
title: marker_series::marker_series (Constructor) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5178b2cebdfa4246256aef6334e026ef091fa553
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "62831418"
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

 **Espacio de nombres**: Concurrency::diagnostic

## <a name="see-also"></a>Vea también
- [Clase marker_series](../profiling/marker-series-class.md)