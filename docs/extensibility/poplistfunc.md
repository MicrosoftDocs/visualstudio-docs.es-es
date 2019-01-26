---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f35ae28a1a231721d5ee5616a3b075737c24e629
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982239"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Esta devolución de llamada se proporciona a la [SccPopulateList](../extensibility/sccpopulatelist-function.md) por el IDE y se usa el complemento de control de origen para actualizar una lista de archivos o directorios (también proporciona a los `SccPopulateList` función).  
  
 Cuando un usuario elige el **obtener** comando en el IDE, el IDE muestra un cuadro de lista de todos los archivos que se puede obtener el usuario. Lamentablemente, el IDE no conoce la lista exacta de todos los archivos que podría obtener el usuario; solo el complemento tiene esta lista. Si otros usuarios han agregado archivos al proyecto de control de código fuente, estos archivos deben aparecer en la lista, pero el IDE no informara de ello. El IDE compila una lista de los archivos que cree que puede obtener el usuario. Antes de esta lista muestra al usuario, llama a la [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` que proporciona el complemento de control de código fuente una oportunidad de agregar y eliminar archivos en la lista.  
  
## <a name="signature"></a>Signatura  
 El complemento de control de origen modifica la lista mediante una llamada a una función implementada por el IDE con el prototipo siguiente:  
  
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
 El `pvCallerData` parámetro pasado por el llamador (IDE) a la [SccPopulateList](../extensibility/sccpopulatelist-function.md). El complemento de control de origen debe asumir nada sobre el contenido de este parámetro.  
  
 fAddRemove  
 Si `TRUE`, `lpFileName` es un archivo que se debe agregar a la lista de archivos. Si `FALSE`, `lpFileName` es un archivo que se debe eliminar de la lista de archivos.  
  
 nStatus  
 Estado de `lpFileName` (una combinación de la `SCC_STATUS` bits; vea [código de estado de archivo](../extensibility/file-status-code-enumerator.md) para obtener más información).  
  
 lpFileName  
 Ruta de acceso completa del directorio del nombre de archivo para agregar o eliminar de la lista.  
  
## <a name="return-value"></a>Valor devuelto  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`TRUE`|El complemento puede seguir llamando a esta función.|  
|`FALSE`|Ha habido un problema en el lado IDE (por ejemplo, de la situación de memoria insuficiente). El complemento debe detenerse la operación.|  
  
## <a name="remarks"></a>Comentarios  
 Para cada archivo que desea que el complemento de control de código fuente para agregar o eliminar de la lista de archivos, llama a esta función, pasando el `lpFileName`. El `fAddRemove` marca indica un archivo nuevo para agregar a la lista o un archivo antiguo para eliminar. El `nStatus` parámetro proporciona el estado del archivo. Cuando haya terminado el complemento de SCC adición y eliminación de archivos, devuelve desde el [SccPopulateList](../extensibility/sccpopulatelist-function.md) llamar.  
  
> [!NOTE]
>  El `SCC_CAP_POPULATELIST` bit de capacidad es necesaria para Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)