---
title: IDebugDocumentHelper::AddDeferredText | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c92909874429075bebc6a1f0a252573d049584e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Notifica a la aplicación auxiliar que el texto dado está disponible, pero no proporciona los caracteres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cChars`  
 [in] Número de caracteres (Unicode) para agregar.  
  
 `dwTextStartCookie`  
 [in] Cookie definidos por el host que representa la posición inicial del texto.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|Error en el método.|  
  
## <a name="remarks"></a>Comentarios  
 Este método permite al host aplazar proporciona los caracteres que se va a agregar hasta que se necesiten, permitiendo que la aplicación auxiliar generar notificaciones precisas y la información de tamaño. El `dwTextStartCookie` parámetro es una cookie, definida por el host, que representa la posición inicial del texto. Las llamadas subsiguientes a `IDebugDocumentText::GetText` debe proporcionar esta cookie. Por ejemplo, en un host que representa el texto en DBCS, la cookie podría ser un desplazamiento de bytes.  
  
 Se supone que una sola llamada a `IDebugDocumentText::GetText` puede obtener caracteres en varias llamadas a `AddDeferredText`. Clases auxiliares también pueden solicitar más de una vez para el mismo intervalo de caracteres diferidas.  
  
> [!NOTE]
>  Las llamadas a `AddDeferredText` no se debe combinar con llamadas a `AddUnicodeText` o `AddDBCSText`. Si esto ocurre, `E_FAIL` se devuelve.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHelper (interfaz)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)