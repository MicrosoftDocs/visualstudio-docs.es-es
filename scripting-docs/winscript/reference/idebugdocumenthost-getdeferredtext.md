---
title: IDebugDocumentHost::GetDeferredText | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ace3bdbfef143a3307d81455788a1e81788cb50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Devuelve un intervalo de caracteres que se han agregado mediante el `IDebugDocumentHelper::AddDeferredText` método, en el documento de host original.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [in] Cookie definidos por el host que representa la posición inicial del texto.  
  
 `pcharText`  
 [entrada, salida] Un búfer de texto de caracteres. Este método no devuelve caracteres si este parámetro es `NULL`.  
  
 `pstaTextAttr`  
 [entrada, salida] Un búfer de atributo de carácter. Este método no devuelve los atributos si este parámetro es `NULL`.  
  
 `pcNumChars`  
 [entrada, salida] Indica el número real de caracteres/atributos devueltos. Este parámetro debe establecerse en cero antes de llamar a este método.  
  
 `cMaxChars`  
 [in] El número máximo de caracteres que se va a devolver.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|No se implementa el método.|  
  
## <a name="remarks"></a>Comentarios  
 Este método puede devolver `E_NOTIMPL`, si el host no llama a `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Este método devuelve el texto del documento original. El host no realizar un seguimiento de cambios u otros cambios en el documento.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHost (interfaz)](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)