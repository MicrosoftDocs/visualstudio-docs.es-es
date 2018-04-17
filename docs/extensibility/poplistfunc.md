---
title: POPLISTFUNC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 950807b0568a28763b369fef4041c69b264d12fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="poplistfunc"></a>POPLISTFUNC
Esta devolución de llamada se proporciona a la [SccPopulateList](../extensibility/sccpopulatelist-function.md) por el IDE y se utiliza el complemento de control de código fuente para actualizar una lista de archivos o directorios (también proporcionado a la `SccPopulateList` función).  
  
 Cuando un usuario elige el **obtener** de comandos en el IDE, el IDE muestra un cuadro de lista de todos los archivos que el usuario puede obtener. Desafortunadamente, el IDE no conoce la lista exacta de todos los archivos que el usuario podría obtener; solo el complemento tiene esta lista. Si otros usuarios han agregado archivos para el proyecto de control de código fuente, estos archivos aparecerán en la lista, pero no conoce el IDE sobre ellos. El IDE compila una lista de los archivos que cree que puede obtener el usuario. Antes de esta lista muestra al usuario, llama a la [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` que proporciona el complemento de control de código fuente una oportunidad para agregar y eliminar archivos de la lista.  
  
## <a name="signature"></a>Signatura  
 El complemento de control de código fuente, modifica la lista mediante una llamada a una función implementada por el IDE con el prototipo siguiente:  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 pvCallerData  
 El `pvCallerData` parámetro pasado por el llamador (el IDE) a la [SccPopulateList](../extensibility/sccpopulatelist-function.md). El complemento de control de código fuente debe suponer nada sobre el contenido de este parámetro.  
  
 fAddRemove  
 Si `TRUE`, `lpFileName` es un archivo que debe agregarse a la lista de archivos. Si `FALSE`, `lpFileName` es un archivo que se debe eliminar de la lista de archivos.  
  
 nStatus  
 Estado de `lpFileName` (una combinación de la `SCC_STATUS` bits; vea [código de estado de archivo](../extensibility/file-status-code-enumerator.md) para obtener más información).  
  
 lpFileName  
 Ruta de acceso completa del directorio del nombre de archivo para agregar o eliminar de la lista.  
  
## <a name="return-value"></a>Valor devuelto  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`TRUE`|El complemento puede seguir llamando a esta función.|  
|`FALSE`|Ha habido un problema en el lado IDE (por ejemplo, un de situación de memoria insuficiente). El complemento debe detener la operación.|  
  
## <a name="remarks"></a>Comentarios  
 Para cada archivo que desea que el complemento de control de código fuente para agregar o eliminar de la lista de archivos, llama a esta función, pasando el `lpFileName`. El `fAddRemove` marca indica un nuevo archivo para agregar a la lista o un archivo antiguo para eliminar. El `nStatus` parámetro indica el estado del archivo. Cuando el complemento de SCC ha terminado de agregar y eliminar archivos, devuelve desde el [SccPopulateList](../extensibility/sccpopulatelist-function.md) llamar.  
  
> [!NOTE]
>  El `SCC_CAP_POPULATELIST` bit de capacidad se requiere para Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)