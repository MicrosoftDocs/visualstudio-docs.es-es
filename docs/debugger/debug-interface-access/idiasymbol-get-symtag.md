---
title: 'Idiasymbol:: Get_symtag | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_symTag method
ms.assetid: 139a35bd-faeb-4878-be72-394dedfbb18f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d3ce5ef46e703cf277dc9eda221a1f4a8426ab3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetsymtag"></a>IDiaSymbol::get_symTag
Recupera el clasificador del tipo de símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_symTag (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve un valor de la [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) enumeración que especifica el clasificador del tipo de símbolo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="example"></a>Ejemplo  
  
```C++  
IDiaSymbol* pType;  
DWORD       tag = 0;  
pType->get_symTag( &tag );  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md)