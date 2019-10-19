---
title: 'IDebugDocumentHelper:: SetDefaultTextAttr | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDefaultTextAttr
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDefaultTextAttr
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea63f028497f1eb90803f59423f608d0a42960cf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574634"
---
# <a name="idebugdocumenthelpersetdefaulttextattr"></a>IDebugDocumentHelper::SetDefaultTextAttr
Establece los atributos predeterminados que se van a usar para el texto que no está en un bloque de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `staTextAttr`  
 Atributos de texto de origen predeterminados.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 A menos que este método cambie los atributos predeterminados, los atributos predeterminados para el texto fuera de un bloque de script son SOURCETEXT_ATTR_NONSOURCE. La interfaz de usuario puede utilizar esta información para marcar el texto fuera de los bloques de scripts como de solo lectura.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)