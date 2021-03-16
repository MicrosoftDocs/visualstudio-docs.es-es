---
description: Inicializa una nueva instancia de la clase span.
title: span::span (Constructor) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fdffdc59b31f5f04817536769d9a712484e6cdd7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223867"
---
# <a name="spanspan-constructor"></a>span::span (Constructor)

Inicializa una nueva instancia de la clase `span`.

## <a name="syntax"></a>Sintaxis

```cpp
span(
   const marker_series& _Series,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parámetros

`_Series` Contexto de la serie de marcador válido.

`_Format` Una cadena de formato compuesto que contiene texto combinado con cero o más elementos de formato, que corresponden a objetos de la lista de argumentos.

`_Importance` Nivel de importancia.

`_Category` Categoría.

## <a name="requirements"></a>Requisitos

**Encabezado:** *cvmarkersobj.h*

**Espacio de nombres:** Concurrency::diagnostic

## <a name="see-also"></a>Consulte también

- [Clase span](../profiling/span-class.md)
