---
title: 'Idiasymbol:: Get_frontendbuild | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_frontEndBuild method
ms.assetid: f7dab1c6-112b-4966-baa5-afc976949c76
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51659c76daac9195223bb4095e48aee56de22cb3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetfrontendbuild"></a>IDiaSymbol::get_frontEndBuild
Recupera el número de compilación de front-end.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_frontEndBuild (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el número de compilación de front-end. Vea la sección Comentarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
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