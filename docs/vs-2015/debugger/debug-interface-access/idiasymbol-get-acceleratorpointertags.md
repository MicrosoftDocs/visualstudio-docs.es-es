---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 829c7a0193ce2742959f677e95dd4a499997cf5b
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "68149841"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Devuelve todos los valores de etiqueta de puntero acelerador que corresponden a una función de código auxiliar del Acelerador C++ AMP.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cnt`  
 [in] El tamaño de la matriz de salida `pPointerTags`.  
  
 `pcnt`  
 [out] El recuento de etiquetas de puntero de Acelerador de la C++ función de código auxiliar del Acelerador de AMP.  
  
 `pPointerTags`  
 [out] Un `DWORD` puntero de matriz que se rellena con los valores de etiqueta del puntero de acelerador en el C++ función de código auxiliar del Acelerador de AMP.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método en un `IDiaSymbol` interfaz que corresponde a una función de código auxiliar del Acelerador C++ AMP.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
