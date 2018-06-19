---
title: Función JsCreateSymbol | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2fccc5d9-f857-46cd-9aeb-f0a2e7cdee6b
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4175f9db664312055fd7260426da227f2a1eb6e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567905"
---
# <a name="jscreatesymbol-function"></a>Función JsCreateSymbol
Crea un símbolo de JavaScript.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsCreateSymbol(  
   _In_ JsValueRef description,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `description`  
 La descripción de cadena del símbolo. Puede ser NULL.  
  
 `result`  
 El nuevo símbolo.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)