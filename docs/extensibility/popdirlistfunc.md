---
title: POPDIRLISTFUNC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: POPLISTFUNC
helpviewer_keywords: POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d5279f16dbc8228f0f116c47e6faa3ab0093472
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Se trata de una función de devolución de llamada dada a la [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) función para actualizar una recopilación de directorios y (opcionalmente) en los nombres de archivo para averiguar lo que están bajo control de código fuente.  
  
 El `POPDIRLISTFUNC` devolución de llamada debe llamarse únicamente para los nombres de archivos y directorios (en la lista dada la `SccPopulateDirList` función) que están realmente bajo control de código fuente.  
  
## <a name="signature"></a>Signatura  
  
```cpp  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 pvCallerData  
 [in] Valor de usuario dado [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bcarpeta  
 [in] `TRUE` si el nombre de `lpDirectoryOrFileName` es un directorio; en caso contrario, el nombre es un nombre de archivo.  
  
 lpDirectoryOrFileName  
 [in] Ruta de acceso local completa de un nombre de directorio o archivo que está bajo control de código fuente.  
  
## <a name="return-value"></a>Valor devuelto  
 El IDE devuelve un código de error correspondiente:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Continuar el procesamiento.|  
|SCC_I_OPERATIONCANCELED|Detiene el procesamiento.|  
|SCC_E_xxx|Cualquier error de control de origen correspondiente debe detener el procesamiento.|  
  
## <a name="remarks"></a>Comentarios  
 Si el `fOptions` parámetro de la `SccPopulateDirList` función contiene el `SCC_PDL_INCLUDEFILES` marca, la lista posiblemente contendrá los nombres de archivo, así como nombres de directorio.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Códigos de error](../extensibility/error-codes.md)