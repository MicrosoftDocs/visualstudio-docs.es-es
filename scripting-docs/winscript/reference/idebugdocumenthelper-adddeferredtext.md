---
title: 'Idebugdocumenthelper:: Adddeferredtext | Documentos de Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba6f945e6c7fa4df83a5e301d73b3fc0bb9da92b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096088"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Notifica a la aplicación auxiliar que el texto dado está disponible, pero no proporciona los caracteres.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cChars`  
 [in] Número de caracteres (Unicode) para agregar.  
  
 `dwTextStartCookie`  
 [in] Cookie definido por el host que representa la posición inicial del texto.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|Error en el método.|  
  
## <a name="remarks"></a>Comentarios  
 Este método permite al host aplazar que proporciona los caracteres que se va a agregar hasta que se necesitan, permitiendo que la aplicación auxiliar generar notificaciones precisas e información de tamaño. El `dwTextStartCookie` parámetro es una cookie, definida por el host, que representa la posición inicial del texto. Las llamadas subsiguientes a `IDebugDocumentText::GetText` debe proporcionar esta cookie. Por ejemplo, en un host que representa el texto en DBCS, la cookie podría ser un desplazamiento de bytes.  
  
 Se supone que una sola llamada a `IDebugDocumentText::GetText` puede obtener los caracteres de varias llamadas a `AddDeferredText`. Clases auxiliares también pueden pedirle más de una vez para el mismo intervalo de caracteres aplazadas.  
  
> [!NOTE]
>  Las llamadas a `AddDeferredText` no deben combinarse con las llamadas a `AddUnicodeText` o `AddDBCSText`. Si esto ocurre, `E_FAIL` se devuelve.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHelper (interfaz)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Idebugdocumenthelper:: Addunicodetext](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [Idebugdocumenthelper:: Adddbcstext](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)