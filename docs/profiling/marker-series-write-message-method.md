---
title: marker_series::write_message (Método) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be6194936264d6038c4dc1e26b5d05f539f0dc6a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "62830907"
---
# <a name="marker_serieswrite_message-method"></a>Método marker_series::write_message
Escribe un mensaje en el archivo de seguimiento del visualizador de simultaneidad.

## <a name="syntax"></a>Sintaxis

```cpp
void write_message(
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parámetros
 `_Format` Una cadena de formato compuesto que contiene texto combinado con cero o más elementos de formato, que corresponden a objetos de la lista de argumentos.

 `_Importance` Nivel de importancia.

 `_Category` Nivel de Category.Importance.

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkersobj.h*

 **Espacio de nombres**: Concurrency::diagnostic

## <a name="see-also"></a>Vea también
- [Clase marker_series](../profiling/marker-series-class.md)