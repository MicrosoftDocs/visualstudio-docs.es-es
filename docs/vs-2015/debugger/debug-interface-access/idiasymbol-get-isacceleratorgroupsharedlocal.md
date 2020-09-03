---
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2e975f75d25e64925c2566c1c311d942e9c3766
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180992"
---
# <a name="idiasymbolget_isacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una marca que indica si el símbolo corresponde a una variable local compartida del grupo en el código compilado para un acelerador de C++ AMP.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT get_isAcceleratorGroupSharedLocal(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFlag`  
 enuncia Un puntero a un `BOOL` que indica si el símbolo corresponde a una variable local compartida del grupo en el código compilado para un acelerador de C++ amp. Si `TRUE` es, `get_baseDataSlot` `get_baseDataOffset` se pueden usar los métodos y para obtener la información de ubicación de almacenamiento para la variable.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol:: get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)   
 [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)
