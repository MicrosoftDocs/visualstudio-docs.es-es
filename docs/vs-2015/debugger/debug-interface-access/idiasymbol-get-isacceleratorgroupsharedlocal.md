---
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8c40b0c28ce99d009a46aa02893dde2f5956c2d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579459"
---
# <a name="idiasymbolgetisacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDiaSymbol::get_isAcceleratorGroupSharedLocal](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal).  
  
Recupera una marca que indica si el símbolo corresponde a una variable local compartida de grupo en el código compilado para un acelerador de AMP de C++.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT get_isAcceleratorGroupSharedLocal(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFlag`  
 [out] Un puntero a un `BOOL` que indica si el símbolo corresponde a una variable local compartida de grupo en el código compilado para un acelerador de AMP de C++. Si `TRUE`, `get_baseDataSlot` y `get_baseDataOffset` pueden usarse los métodos para obtener la información de ubicación de almacenamiento para la variable.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)   
 [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)



