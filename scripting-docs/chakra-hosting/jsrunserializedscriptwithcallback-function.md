---
title: "Función JsRunSerializedScriptWithCallback | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0608d778-f65b-4dc5-a745-364aac57ef59
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce51c9473100e71831dd53cc6572d9740790ffa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsrunserializedscriptwithcallback-function"></a>JsRunSerializedScriptWithCallback (función)
Ejecuta un script serializado.     Proporciona la capacidad de hacer una carga diferida del origen del script solo cuando sea necesario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_opt_ JsValueRef *result  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `scriptLoadCallback`  
 La devolución de la llamada se hace cuando debe cargarse el código fuente del script.  
  
 `scriptUnloadCallback`  
 La devolución de la llamada se hace cuando el script serializado y el código fuente ya no son necesarios.  
  
 `buffer`  
 El script serializado.  
  
 `sourceContext`  
 Cookie que identifica el script que pueden usar los contextos de script depurables.     Este contexto pasará a scriptLoadCallback y scriptUnloadCallback.  
  
 `sourceUrl`  
 La ubicación de procedencia del script.  
  
 `result`  
 El resultado de la ejecución del script, si existe. Este parámetro puede ser NULL.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Esta API no está disponible para aplicaciones de la Tienda.  
  
 Requiere un contexto de script activo.  
  
 El tiempo de ejecución conservará el búfer hasta que se realice la recolección de elementos no utilizados de todas las instancias de cualquier función creada desde el búfer.  Luego llamará a scriptUnloadCallback para informar al autor de la llamada de que es seguro liberar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)