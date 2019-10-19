---
title: 'Iactivescriptauthor (:: GetScriptletTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cd0090b9ade47ad37acf6d285ec7f072f1ea5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576168"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Devuelve los atributos de texto de un Scriptlet.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszCode`  
 [in, size_is (`cch`)] El texto del Scriptlet. Esta cadena no tiene que estar terminada en NULL.  
  
 `cch`  
 de Tamaño utilizado para los parámetros `pszCode` y `pattr`.  
  
 `pszDelimiter`  
 de Dirección del delimitador de fin de Scriptlet. Cuando `pszCode` se analiza desde un flujo de texto, el host normalmente usa un delimitador (como dos comillas simples) para detectar el final del Scriptlet. Establezca este parámetro en NULL si no se usa ningún delimitador para identificar el final del Scriptlet.  
  
 `dwFlags`  
 de Marcas que están asociadas a los atributos de texto del Scriptlet. Puede ser una combinación de los valores siguientes.  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identificar los identificadores que tienen el atributo SOURCETEXT_ATTR_IDENTIFIER e identificar los operadores de puntos que tienen el atributo SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Identifique el objeto actual que tiene el atributo SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identifique el contenido de la cadena y el texto del comentario que tenga el atributo SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] La información de color para el código Scriptlet.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iactivescriptauthor (](../../winscript/reference/iactivescriptauthor-interface.md)  
 [Iactivescriptauthor (:: GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)    
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)