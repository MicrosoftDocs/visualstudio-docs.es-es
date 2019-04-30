---
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edbd1d8ae66e58611ab538cf0bfe695cb22b3412
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63400879"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Recupera el tipo de un puntero a la tabla base virtual.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`pRetVal`|[out] Devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que especifica el tipo de tabla base.|

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 Un puntero a la tabla base virtual (`vbtptr`) es un puntero oculto en un [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable que controla la herencia de clases base virtuales. Un `vbtptr` puede tener diferentes tamaños según las clases heredadas.

 Este método devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que puede usarse para determinar el tamaño de la vbtptr.

## <a name="requirements"></a>Requisitos

|Requisito|Descripción|
|-----------------|-----------------|
|Encabezado:|dia2.h|
|Versión:|SDK de DIA v8.0|

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)