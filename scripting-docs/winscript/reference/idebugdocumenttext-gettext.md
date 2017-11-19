---
title: IDebugDocumentText::GetText | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentText.GetText
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a1006304974fab4959ad6313ffdc26793cdd345
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Recupera los caracteres o los atributos de carácter asociados a un intervalo de posición de carácter.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cCharacterPosition`  
 [in] Iniciar ubicación la posición del intervalo de caracteres.  
  
 `pcharText`  
 [entrada, salida] Un búfer de texto de caracteres. El búfer debe ser lo suficientemente grande como para contener `cMaxChars` caracteres. Si este parámetro es NULL, el método no devuelve los caracteres.  
  
 `pstaTextAttr`  
 [entrada, salida] Un búfer de atributo de carácter. El búfer debe ser lo suficientemente grande como para contener `cMaxChars` caracteres. Si este parámetro es NULL, el método no devuelve los atributos.  
  
 `pcNumChars`  
 [entrada, salida] Devuelve el número de caracteres o atributos. Este parámetro debe establecerse en cero antes de llamar a este método.  
  
 `cMaxChars`  
 [in] Número de caracteres en el intervalo de la posición de carácter. También especifica el número máximo de caracteres que se va a devolver.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método recupera los caracteres o los atributos de carácter asociados a un intervalo de posición de carácter. El intervalo de la posición de caracteres se especifica mediante una posición de carácter y un número de caracteres.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentText (interfaz)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)