---
title: "Función JsCreateNamedFunction | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72f40d06-ab82-4fed-a632-68af6b4126c2
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a55f3df1d086394a7431b355f037b33e3f4a86c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jscreatenamedfunction-function"></a>Función JsCreateNamedFunction
Crea una nueva función de JavaScript con nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateNamedFunction(  
   _In_ JsValueRef name,  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `name`  
 El nombre de esta función que se utilizará para diagnósticos y convertir en cadena.  
  
 `nativeFunction`  
 Método al que se llama cuando se invoca la función.  
  
 `callbackState`  
 Estado proporcionado por el usuario que se pasará de nuevo a la devolución de llamada.  
  
 `function`  
 Nuevo objeto de función.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)