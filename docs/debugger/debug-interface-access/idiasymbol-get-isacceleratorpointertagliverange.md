---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2434dac0a4f0e4d9ff1c998f0cd70da4f9c558b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetisacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Recupera una marca que indica si el símbolo corresponde a la *símbolo de definición de intervalo* para el componente de etiqueta de una variable de puntero en el código compilado para un acelerador de AMP de C++. El símbolo de definición de intervalo es la ubicación de una variable para un intervalo de direcciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_isAcceleratorPointerTagLiveRange(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFlag`  
 [out] Un puntero a un `BOOL` que indica si el símbolo se corresponde con el símbolo de definición de intervalo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)