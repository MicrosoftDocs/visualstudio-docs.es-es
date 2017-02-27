---
title: "POPLISTFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "POPDIRLISTFUNC"
helpviewer_keywords: 
  - "Función de devolución de llamada POPLISTFUNC"
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# POPLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta devolución de llamada se proporciona a la [SccPopulateList](../extensibility/sccpopulatelist-function.md) por el IDE y se utiliza el complemento de control de origen para actualizar una lista de archivos o directorios \(también proporciona a los `SccPopulateList` función\).  
  
 Cuando un usuario elige el **obtener** de comandos en el IDE, el IDE muestra un cuadro de lista de todos los archivos que el usuario puede obtener. Lamentablemente, el IDE no conoce la lista exacta de todos los archivos que el usuario podría obtener; solo el complemento tiene esta lista. Si otros usuarios han agregado archivos para el proyecto de control de código fuente, estos archivos deben aparecer en la lista, pero el IDE no saben de ellos. El IDE compila una lista de los archivos que cree que puede obtener el usuario. Antes de esta lista muestra al usuario, llama a la [SccPopulateList](../extensibility/sccpopulatelist-function.md)`,` que proporciona el complemento de control de código fuente una oportunidad de agregar y eliminar archivos de la lista.  
  
## Signature  
 El complemento de control de código fuente, modifica la lista mediante una llamada a una función implementada por el IDE con el prototipo siguiente:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) ( LPVOID pvCallerData, BOOL fAddRemove, LONG nStatus, LPSTR lpFileName );  
```  
  
## Parámetros  
 pvCallerData  
 El `pvCallerData` parámetro pasado por el llamador \(IDE\) a la [SccPopulateList](../extensibility/sccpopulatelist-function.md). El complemento de control de código fuente debe suponer nada sobre el contenido de este parámetro.  
  
 fAddRemove  
 Si `TRUE`, `lpFileName` es un archivo que debe agregarse a la lista de archivos. Si `FALSE`, `lpFileName` es un archivo que debe eliminarse de la lista de archivos.  
  
 nStatus  
 Estado de `lpFileName` \(una combinación de la `SCC_STATUS` bits; vea [Código de estado de archivo](../extensibility/file-status-code-enumerator.md) para obtener más información\).  
  
 lpFileName  
 Ruta de acceso completa del nombre de archivo para agregar o eliminar de la lista.  
  
## Valor devuelto  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`TRUE`|El complemento puede seguir llamando a esta función.|  
|`FALSE`|Ha habido un problema en el lado del IDE \(por ejemplo, un de situación de memoria insuficiente\). El complemento debe detener la operación.|  
  
## Comentarios  
 Para cada archivo que desea que el complemento de control de código fuente para agregar o eliminar de la lista de archivos, llama a esta función, pasando el `lpFileName`. El `fAddRemove` marca indica un nuevo archivo para agregar a la lista o un archivo antiguo para eliminar. El `nStatus` parámetro indica el estado del archivo. Cuando el complemento control de código fuente ha terminado de agregar y eliminar archivos, devuelve desde el [SccPopulateList](../extensibility/sccpopulatelist-function.md) llamar.  
  
> [!NOTE]
>  El `SCC_CAP_POPULATELIST` bit de capacidad se requiere para Visual Studio.  
  
## Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)