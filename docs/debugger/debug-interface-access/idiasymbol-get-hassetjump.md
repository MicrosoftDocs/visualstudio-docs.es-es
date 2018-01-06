---
title: 'Idiasymbol:: Get_hassetjump | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_hasSetJump method
ms.assetid: 22656206-dccf-40ed-b179-fc016d1b262a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d6d7141e6dd97fbe4c1d7b3df9a2d245e2abe3d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgethassetjump"></a>IDiaSymbol::get_hasSetJump
Recupera una marca que especifica si la función contiene un uso de la [setjmp](/cpp/c-runtime-library/reference/setjmp) comando (emparejado con el [longjmp](/cpp/c-runtime-library/reference/longjmp) comando ellos forman el método de estilo C de control de excepciones).  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_hasSetJump(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFlag`  
 [out] Devuelve `TRUE` si la función contiene un `setjmp` comando; de lo contrario, devuelve `FALSE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|dia2.h|  
|Versión:|SDK de DIA v8.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol:: Get_haslongjump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)   
 [longjmp](/cpp/c-runtime-library/reference/longjmp)   
 [setjmp](/cpp/c-runtime-library/reference/setjmp)