---
title: IDiaSymbol::get_backEndMinor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db90118a1c8d235637f78edd9daa51f3531c628d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843178"
---
# <a name="idiasymbolget_backendminor"></a>IDiaSymbol::get_backEndMinor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el número de versión secundaria de back-end del compilador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 enuncia Devuelve el número de versión secundaria de back-end. Vea la sección Comentarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Notas  
 Un compilador normalmente se compone de dos elementos principales: el front-end (el analizador), que controla el análisis del código fuente en un formato intermedio y un back-end (generador de código), que convierte el formato intermedio en ensamblado. No es raro que el front-end tenga una versión diferente que el back-end.  
  
 Un número de versión de front-end o back-end consta de tres partes: \<major> . \<minor> . \<build> , donde \<major> es el número de versión principal, \<minor> es el número de versión secundaria y \<build> es el número de compilación. Por ejemplo, 13.10.3077.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|dia2.h|  
|Versión:|SDK de DIA v 7.0|  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
