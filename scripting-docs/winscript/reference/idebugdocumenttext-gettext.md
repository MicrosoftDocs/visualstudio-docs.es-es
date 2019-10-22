---
title: 'IDebugDocumentText:: GetText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e6472c40802fff4dad6e5ecc8f2729c95459e09f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572073"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Recupera los caracteres y/o los atributos de carácter asociados a un intervalo de posiciones de caracteres.  
  
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
 de Ubicación de inicio del intervalo de posición de caracteres.  
  
 `pcharText`  
 [in, out] Un búfer de texto de caracteres. El búfer debe ser lo suficientemente grande como para contener `cMaxChars` caracteres. Si este parámetro es NULL, el método no devuelve caracteres.  
  
 `pstaTextAttr`  
 [in, out] Un búfer de atributo de carácter. El búfer debe ser lo suficientemente grande como para contener `cMaxChars` caracteres. Si este parámetro es NULL, el método no devuelve atributos.  
  
 `pcNumChars`  
 [in, out] Número de caracteres o atributos devueltos. Este parámetro debe establecerse en cero antes de llamar a este método.  
  
 `cMaxChars`  
 de Número de caracteres del intervalo de posición de caracteres. También especifica el número máximo de caracteres que se van a devolver.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método recupera los caracteres y/o los atributos de carácter asociados a un intervalo de posiciones de caracteres. El intervalo de posición de caracteres se especifica mediante una posición de carácter y un número de caracteres.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)  
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)