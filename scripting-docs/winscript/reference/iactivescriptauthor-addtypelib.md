---
title: IActiveScriptAuthor::AddTypeLib | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 150628f1822c721f1e349005de457951e226ef1b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645625"
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
Agrega una biblioteca de tipos para el espacio de nombres para la secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rguidTypeLib`  
 [in] El CLSID (identificador de clase) de la biblioteca de tipos que se va a agregar.  
  
 `dwMajor`  
 [in] El número de versión principal.  
  
 `dwMinor`  
 [in] El número de versión secundaria.  
  
 `dwFlags`  
 [in] No usado.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método llama a `LoadTypeLib` para cargar la biblioteca de tipos. Cuando se realiza correctamente, este método llama a `IActiveScriptAuthor::AddNamedItem` para agregar información de tipo.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](http://msdn.microsoft.com/en-us/155b48e5-5438-409e-9342-630a6a500f60)