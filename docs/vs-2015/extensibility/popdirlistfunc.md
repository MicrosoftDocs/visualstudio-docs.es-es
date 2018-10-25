---
title: POPDIRLISTFUNC | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4afd84af0ab6d7f801c486dd506ca5d5a10f6909
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867967"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta es una función de devolución de llamada a la [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) función para actualizar una colección de los directorios y (opcionalmente) los nombres de archivo para averiguar lo que están bajo control de código fuente.  
  
 El `POPDIRLISTFUNC` devolución de llamada debe llamarse únicamente para los nombres de archivos y directorios (en la lista proporcionada para el `SccPopulateDirList` función) que realmente están bajo control de código fuente.  
  
## <a name="signature"></a>Signatura  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 pvCallerData  
 [in] Valor del usuario [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bcarpeta  
 [in] `TRUE` si el nombre en `lpDirectoryOrFileName` es un directorio; en caso contrario, el nombre es un nombre de archivo.  
  
 lpDirectoryOrFileName  
 [in] Ruta de acceso local completa en un nombre de directorio o archivo que está bajo control de código fuente.  
  
## <a name="return-value"></a>Valor devuelto  
 El IDE devuelve un código de error adecuado:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Continuar el procesamiento.|  
|SCC_I_OPERATIONCANCELED|Detener el procesamiento.|  
|SCC_E_xxx|Cualquier error de control de origen adecuado debe detener el procesamiento.|  
  
## <a name="remarks"></a>Comentarios  
 Si el `fOptions` parámetro de la `SccPopulateDirList` función contiene el `SCC_PDL_INCLUDEFILES` marca, a continuación, la lista contendrá, posiblemente, los nombres de archivo, así como los nombres de directorio.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Códigos de error](../extensibility/error-codes.md)

