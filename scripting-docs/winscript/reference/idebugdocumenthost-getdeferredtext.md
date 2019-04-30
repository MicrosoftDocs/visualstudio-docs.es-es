---
title: IDebugDocumentHost::GetDeferredText | Microsoft Docs
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
ms.openlocfilehash: 3e5800a6de15d2d59208022fa44d3c2f4c931e14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446571"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Devuelve un rango de caracteres que se han agregado mediante el `IDebugDocumentHelper::AddDeferredText` método, en el documento de host original.  
  
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
 [in] Cookie definido por el host que representa la posición inicial del texto.  
  
 `pcharText`  
 [in, out] Un búfer de texto del carácter. Este método no devuelve caracteres si este parámetro es `NULL`.  
  
 `pstaTextAttr`  
 [in, out] Un búfer de atributo de caracteres. Este método no devuelve los atributos si este parámetro es `NULL`.  
  
 `pcNumChars`  
 [in, out] Indica el número real de caracteres y los atributos devueltos. Este parámetro debe establecerse en cero antes de llamar a este método.  
  
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
> Este método devuelve el texto del documento original. El host no realizar un seguimiento de las modificaciones u otros cambios en el documento.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHost (interfaz)](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)