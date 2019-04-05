---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4969dff811b6517c0274a35884703a9dc0c693cb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988311"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se trata de una función de devolución de llamada especificada en una llamada a la [SccSetOption](../extensibility/sccsetoption-function.md) (mediante la opción `SCC_OPT_NAMECHANGEPFN`) y se usa para comunicar los cambios de nombre mediante el control de código fuente complemento vuelve a realizar el IDE.  
  
## <a name="signature"></a>Signatura  
  
```cpp#  
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
 [in] Se ha cambiado el nombre del archivo a.  
  
## <a name="return-value"></a>Valor devuelto  
 Ninguno.  
  
## <a name="remarks"></a>Comentarios  
 Si se cambia el nombre de un archivo durante una operación de control de código fuente, el complemento de control de código fuente puede notificar el IDE sobre el cambio de nombre a través de esta devolución de llamada.  
  
 Si el IDE no admite esta devolución de llamada, no llamará a la [SccSetOption](../extensibility/sccsetoption-function.md) para especificarla. Si el complemento no admite esta devolución de llamada, devolverá `SCC_E_OPNOTSUPPORTED` desde el `SccSetOption` funcionar cuando el IDE intenta establecer la devolución de llamada.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
