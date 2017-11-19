---
title: OPTNAMECHANGEPFN | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OPTNAMECHANGEPFN
helpviewer_keywords: OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 666174c4f0f54679907bd239a81c5c369dc09a3d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Se trata de una función de devolución de llamada especificada en una llamada a la [SccSetOption](../extensibility/sccsetoption-function.md) (mediante la opción `SCC_OPT_NAMECHANGEPFN`) y se usa para comunicar los cambios de nombre realizados por el control de código fuente complemento volver al IDE.  
  
## <a name="signature"></a>Signatura  
  
```cpp  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 pvCallerData  
 [in] Valor de usuario especificado en una llamada anterior a la [SccSetOption](../extensibility/sccsetoption-function.md) (mediante la opción `SCC_OPT_USERDATA`).  
  
 pszOldName  
 [in] El nombre original del archivo.  
  
 pszNewName  
 [in] El nombre del archivo se ha cambiado a.  
  
## <a name="return-value"></a>Valor devuelto  
 Ninguno.  
  
## <a name="remarks"></a>Comentarios  
 Si se cambia el nombre de un archivo durante una operación de control de código fuente, el complemento de control de código fuente puede notificar el IDE sobre el cambio de nombre a través de esta devolución de llamada.  
  
 Si el IDE no admite esta devolución de llamada, no llamará a la [SccSetOption](../extensibility/sccsetoption-function.md) que se especifique. Si el complemento no admite esta devolución de llamada, devolverá `SCC_E_OPNOTSUPPORTED` desde el `SccSetOption` funcionar cuando el IDE intenta establecer la devolución de llamada.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)