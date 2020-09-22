---
title: IDiaSymbol::get_lowerBound | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lowerBound method
ms.assetid: e9a6440b-d068-4de4-a240-6723d20812b9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cab01c4ee80b269dd51d0da809ab9e33460a1e60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843127"
---
# <a name="idiasymbolget_lowerbound"></a>IDiaSymbol::get_lowerBound
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el límite inferior de una dimensión de matriz FORTRAN.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_lowerBound (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 enuncia Devuelve un objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el límite inferior de una dimensión de matriz Fortran.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
