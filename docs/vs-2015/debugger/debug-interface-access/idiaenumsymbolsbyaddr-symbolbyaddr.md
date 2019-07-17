---
title: IDiaEnumSymbolsByAddr::symbolByAddr | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByAddr method
ms.assetid: 0b6f5a68-8402-4f29-8219-20576fda8166
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6561c3afd273a2a559138ed2363b4ffa4fdd0fd8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189607"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyaddr"></a>IDiaEnumSymbolsByAddr::symbolByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Coloca el enumerador realizando una búsqueda por número de la sección de imagen y el desplazamiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT symbolByAddr (   
   DWORD**      isect,  
   DWORD**      offsect,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 isect  
 [in] Número de la sección de imagen.  
  
 offsect  
 [in] Desplazamiento en la sección.  
  
 ppsymbol  
 [out] Devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa el símbolo se encuentra.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se encontró el símbolo. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
