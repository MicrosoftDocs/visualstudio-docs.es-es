---
title: 'IDebugDocumentHelper:: AddDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1aae73e44059b1f07fa4cb54f40cdcd12e564a8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577039"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Notifica a la aplicación auxiliar que el texto especificado está disponible, pero no proporciona los caracteres.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cChars`  
 de Número de caracteres (Unicode) que se van a agregar.  
  
 `dwTextStartCookie`  
 de Cookie definida por el host que representa la posición inicial del texto.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|Error en el método.|  
  
## <a name="remarks"></a>Comentarios  
 Este método permite al host aplazar la entrega de los caracteres que se van a agregar hasta que sean necesarios, a la vez que permite que el ayudante genere notificaciones precisas e información de tamaño. El parámetro `dwTextStartCookie` es una cookie, definida por el host, que representa la posición inicial del texto. Las llamadas subsiguientes a `IDebugDocumentText::GetText` deben proporcionar esta cookie. Por ejemplo, en un host que representa texto en DBCS, la cookie podría ser un desplazamiento de bytes.  
  
 Se supone que una única llamada a `IDebugDocumentText::GetText` puede obtener caracteres de varias llamadas a `AddDeferredText`. Las clases auxiliares también pueden solicitar el mismo intervalo de caracteres diferidos más de una vez.  
  
> [!NOTE]
> Las llamadas a `AddDeferredText` no deben combinarse con llamadas a `AddUnicodeText` o `AddDBCSText`. Si esto ocurre, se devuelve `E_FAIL`.  
  
## <a name="see-also"></a>Vea también  
   de la [interfaz IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)