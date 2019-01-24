---
title: IDiaSymbol::get_acceleratorPointerTags | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efad3aeaf0d8a30d521d16612639d0b663ee8ebe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720677"
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
 [out] El recuento de etiquetas de puntero de Acelerador de la función de código auxiliar del Acelerador C++ AMP.  
  
 `pPointerTags`  
 [out] Un `DWORD` puntero de matriz que se rellena con los valores de etiqueta del puntero de Acelerador de la función de código auxiliar de acelerador C++ AMP.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método en un `IDiaSymbol` interfaz que corresponde a una función de código auxiliar del Acelerador C++ AMP.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



