---
title: span::span (Constructor) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df6df731de90a9aad9e6cc637b3f218e481b66b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198296"
---
# <a name="spanspan-constructor"></a>span::span (Constructor)

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inicializa una nueva instancia de la clase `span`.

## <a name="syntax"></a>Sintaxis

```
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

**Encabezado:** cvmarkersobj.h

**Espacio de nombres**: Concurrency::diagnostic

## <a name="see-also"></a>Consulte también

[span (clase)](../profiling/span-class.md)
