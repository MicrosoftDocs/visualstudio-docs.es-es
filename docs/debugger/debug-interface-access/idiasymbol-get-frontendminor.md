---
title: 'Idiasymbol:: Get_frontendminor | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1f276239d76f02b9db68f7acacc52e693056f061
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetfrontendminor"></a>IDiaSymbol::get_frontEndMinor
Recupera el número de versión secundaria de front-end.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el número de versión secundaria de front.end.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Un compilador normalmente se compone de dos elementos principales: el front-end (el analizador), que se encarga de analizar el código fuente en un formato intermedio, y un back-end (generador de código), que convierte el formato intermedio en el ensamblado. No es raro que el front-end tenga una versión diferente que el back-end.  
  
 Un front-end o un número de versión de back-end se compone de tres partes: \<principal >.\< secundaria >. \<generar >, donde \<principales > es el número de versión principal, \<secundaria > es el número de versión secundaria, y \<de compilación > es el número de compilación. Por ejemplo, 13.10.3077.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|dia2.h|  
|Versión:|SDK de DIA v7.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)