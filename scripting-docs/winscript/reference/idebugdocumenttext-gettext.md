---
title: IDebugDocumentText::GetText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77cc255bcd04754cbfde4638b67a85f6fdc0a922
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091993"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Recupera los caracteres o los atributos de carácter asociados a un intervalo de la posición del carácter.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 [in] Inicie la ubicación de la posición del intervalo de caracteres.  
  
 `pcharText`  
 [in, out] Un búfer de texto del carácter. El búfer debe ser lo suficientemente grande como para contener `cMaxChars` caracteres. Si este parámetro es NULL, el método no devuelve caracteres.  
  
 `pstaTextAttr`  
 [in, out] Un búfer de atributo de caracteres. El búfer debe ser lo suficientemente grande como para contener `cMaxChars` caracteres. Si este parámetro es NULL, el método no devuelve los atributos.  
  
 `pcNumChars`  
 [in, out] Devuelve el número de caracteres o atributos. Este parámetro debe establecerse en cero antes de llamar a este método.  
  
 `cMaxChars`  
 [in] Número de caracteres en el intervalo de la posición de carácter. También especifica el número máximo de caracteres que se va a devolver.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método recupera los caracteres o los atributos de carácter asociados a un intervalo de la posición del carácter. El intervalo de la posición de carácter especificado por una posición de carácter y un número de caracteres.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentText (interfaz)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)