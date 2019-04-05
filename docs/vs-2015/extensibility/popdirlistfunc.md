---
title: POPDIRLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77e4701d3d8ec54fd37d6483f55b10a28af65b15
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987182"
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
  
 bFolder  
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
