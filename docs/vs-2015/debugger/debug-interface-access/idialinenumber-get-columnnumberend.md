---
title: IDiaLineNumber::get_columnNumberEnd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d6fb8cb5b3cfa7aa741db4e49dc7c2b3e1daee4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192351"
---
# <a name="idialinenumberget_columnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el número de columna de origen basado en uno en el que finaliza la expresión o instrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 enuncia Devuelve el número de columna donde finaliza la expresión o instrucción. Si el valor es cero, la información de finalización de la columna no está presente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 El valor de columna devuelto por este método es un desplazamiento de bytes en la línea a la posición posterior al último carácter de la instrucción de la línea.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
