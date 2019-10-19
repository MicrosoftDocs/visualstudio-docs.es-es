---
title: 'IDebugDocumentHost:: GetDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 273b4eb52b7263d34c347dff3a00479945b809df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569424"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Devuelve un intervalo de caracteres que se agregaron mediante el método `IDebugDocumentHelper::AddDeferredText` en el documento host original.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwTextStartCookie`  
 de Cookie definida por el host que representa la posición inicial del texto.  
  
 `pcharText`  
 [in, out] Un búfer de texto de caracteres. Este método no devuelve caracteres si este parámetro es `NULL`.  
  
 `pstaTextAttr`  
 [in, out] Un búfer de atributo de carácter. Este método no devuelve atributos si este parámetro es `NULL`.  
  
 `pcNumChars`  
 [in, out] Indica el número real de caracteres o atributos devueltos. Este parámetro debe establecerse en cero antes de llamar a este método.  
  
 `cMaxChars`  
 de Número máximo de caracteres que se van a devolver.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|No se ha implementado el método.|  
  
## <a name="remarks"></a>Comentarios  
 Este método puede devolver `E_NOTIMPL`, si el host no llama a `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
> Este método devuelve el texto del documento original. El host no realiza un seguimiento de las ediciones u otros cambios en el documento.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)  
 [IDebugDocumentHelper:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)