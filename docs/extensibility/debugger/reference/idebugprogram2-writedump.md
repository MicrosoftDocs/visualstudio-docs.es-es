---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3d2953b3f30a0d485b58afc04e8ce42158a7537e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905277"
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
 [in] La dirección URL para escribir el volcado. Normalmente, esto es en forma de `file://c:\path\filename.ext`, pero puede ser cualquier dirección URL válida.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Un volcado de memoria de programa normalmente incluiría el marco de pila actual, la propia pila, una lista de los subprocesos que se ejecutan en el programa y, posiblemente, toda la memoria que posee el programa.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)