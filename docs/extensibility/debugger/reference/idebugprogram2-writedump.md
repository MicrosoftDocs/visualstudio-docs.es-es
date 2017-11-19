---
title: IDebugProgram2::WriteDump | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::WriteDump
helpviewer_keywords: IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b68392d94b16f13106e421c5d466e3fbdf4a2b27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Escribe un volcado de memoria en un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `DumpType`  
 [in] Un valor de la [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) enumeración que especifica el tipo de volcado de memoria, por ejemplo, short o long.  
  
 `pszDumpUrl`  
 [in] La dirección URL para escribir en el volcado de memoria. Normalmente, esto es en forma de `file://c:\path\filename.ext`, pero puede ser cualquier dirección URL válida.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Un volcado de memoria de programa normalmente incluiría el marco de pila actual, la propia pila, una lista de los subprocesos que se ejecutan en el programa y posiblemente toda la memoria que posee el programa.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)