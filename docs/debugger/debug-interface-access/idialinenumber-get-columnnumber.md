---
title: IDiaLineNumber::get_columnNumber | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03d24770c90ebd225fa37dd7f60d794781e79e7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828451"
---
# <a name="idialinenumbergetcolumnnumber"></a>IDiaLineNumber::get_columnNumber
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el número de columna donde comienza la expresión o instrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[C++]  
HRESULT get_columnNumber (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el número de columna donde comienza la expresión o instrucción. Si el valor es cero, la información de columna no está presente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El valor de columna devuelto por este método es un desplazamiento de bytes en la línea al primer carácter de la instrucción en la línea.  
  
## <a name="see-also"></a>Vea también  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
