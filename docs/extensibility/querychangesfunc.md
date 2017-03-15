---
title: "QUERYCHANGESFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "QUERYCHANGESFUNC"
helpviewer_keywords: 
  - "Función de devolución de llamada QUERYCHANGESFUNC"
  - "Estructura QUERYCHANGESDATA"
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se trata de una función de devolución de llamada que se utiliza la [SccQueryChanges](../extensibility/sccquerychanges-function.md) operación para enumerar una colección de nombres de archivo y determinar el estado de cada archivo.  
  
 El `SccQueryChanges` tiene una lista de archivos y un puntero a función el `QUERYCHANGESFUNC` devolución de llamada. El complemento de control de código fuente enumera la lista determinada y proporciona un estado \(a través de esta devolución de llamada\) para cada archivo en la lista.  
  
## Signature  
  
```cpp#  
typedef BOOL (*QUERYCHANGESFUNC)( LPVOID pvCallerData, QUERYCHANGESDATA * pChangesData );  
```  
  
## Parámetros  
 pvCallerData  
 \[in\] El `pvCallerData` parámetro pasado por el llamador \(IDE\) a [SccQueryChanges](../extensibility/sccquerychanges-function.md). El complemento de control de código fuente debe hacer ninguna suposición sobre el contenido de este valor.  
  
 pChangesData  
 \[in\] Puntero a un [QUERYCHANGESDATA (estructura)](#LinkQUERYCHANGESDATA) estructura que describe los cambios en un archivo.  
  
## Valor devuelto  
 El IDE devuelve un código de error adecuado:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Continuar el procesamiento.|  
|SCC\_I\_OPERATIONCANCELED|Detener el procesamiento.|  
|SCC\_E\_xxx|Cualquier error de SCC apropiado debe detener el procesamiento.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA \(estructura\)  
 La estructura que se pasa para cada archivo tiene el siguiente aspecto:  
  
```cpp#  
struct QUERYCHANGESDATA_A { DWORD  dwSize; LPCSTR lpFileName; DWORD  dwChangeType; LPCSTR lpLatestName; }; typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA; struct QUERYCHANGESDATA_W { DWORD   dwSize; LPCWSTR lpFileName; DWORD   dwChangeType; LPCWSTR lpLatestName; };  
```  
  
 dwSize  
 Tamaño de esta estructura \(en bytes\).  
  
 lpFileName  
 El nombre de archivo original para este elemento.  
  
 dwChangeType  
 Código que indica el estado del archivo:  
  
|Código|Descripción|  
|------------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|No puede saber qué ha cambiado.|  
|`SCC_CHANGE_UNCHANGED`|No hay cambios de nombre de este archivo.|  
|`SCC_CHANGE_DIFFERENT`|Archivo con una identidad diferente, pero el mismo nombre existe en la base de datos.|  
|`SCC_CHANGE_NONEXISTENT`|Archivo no existe en la base de datos o localmente.|  
|`SCC_CHANGE_DATABASE_DELETED`|Archivo eliminado en la base de datos.|  
|`SCC_CHANGE_LOCAL_DELETED`|Archivo eliminado localmente, pero el archivo sigue existiendo en la base de datos. Si no puede determinarse, devolver `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Archivo agregado a la base de datos, pero no existe localmente.|  
|`SCC_CHANGE_LOCAL_ADDED`|Archivo no existe en la base de datos y un nuevo archivo local.|  
|`SCC_CHANGE_RENAMED_TO`|Archivo cambiado de nombre o en la base de datos como `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Mover en la base de datos o cambiar el nombre de archivo `lpLatestName`; Si es demasiado costosa para realizar un seguimiento, devuelve un indicador diferente, como `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 El nombre de archivo actual de este elemento.  
  
## Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Códigos de error](../extensibility/error-codes.md)