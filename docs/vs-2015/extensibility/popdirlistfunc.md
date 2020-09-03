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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194051"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se trata de una función de devolución de llamada proporcionada a la función [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) para actualizar una colección de directorios y (opcionalmente) nombres de archivo para averiguar cuáles están bajo control de código fuente.  
  
 `POPDIRLISTFUNC`Solo se debe llamar a la devolución de llamada para esos directorios y nombres de archivo (en la lista proporcionada a la `SccPopulateDirList` función) que realmente están bajo control de código fuente.  
  
## <a name="signature"></a>Firma  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 pvCallerData  
 de Valor de usuario dado a [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bFolder  
 [in] `TRUE` Si el nombre de `lpDirectoryOrFileName` es un directorio; de lo contrario, el nombre es un nombre de archivo.  
  
 lpDirectoryOrFileName  
 de Ruta de acceso local completa a un directorio o nombre de archivo que se encuentra bajo control de código fuente.  
  
## <a name="return-value"></a>Valor devuelto  
 El IDE devuelve un código de error adecuado:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|Continúe el procesamiento.|  
|SCC_I_OPERATIONCANCELED|Detiene el procesamiento.|  
|SCC_E_xxx|Cualquier error de control de código fuente adecuado debe detener el procesamiento.|  
  
## <a name="remarks"></a>Comentarios  
 Si el `fOptions` parámetro de la `SccPopulateDirList` función contiene la `SCC_PDL_INCLUDEFILES` marca, la lista posiblemente contendrá nombres de archivo y nombres de directorio.  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Códigos de error](../extensibility/error-codes.md)
