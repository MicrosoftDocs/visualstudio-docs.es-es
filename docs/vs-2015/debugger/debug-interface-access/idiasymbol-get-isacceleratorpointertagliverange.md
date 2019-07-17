---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5a53faf8c9395867b570909ac4d34cf329da12c6
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "68149456"
---
# <a name="idiasymbolgetisacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una marca que indica si el símbolo corresponde a la *símbolo de definición intervalo* para el componente de la etiqueta de una variable de puntero en el código compilado para un acelerador de AMP de C++. El símbolo de intervalo de definición es la ubicación de una variable para un intervalo de direcciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT get_isAcceleratorPointerTagLiveRange(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFlag`  
 [out] Un puntero a un `BOOL` que indica si el símbolo se corresponde con el símbolo de intervalo de definición.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
