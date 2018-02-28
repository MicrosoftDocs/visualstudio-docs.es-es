---
title: QUERYCHANGESFUNC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 43add362011b31ce695e9a8d9e77d6ca2dedb0e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Se trata de una función de devolución de llamada utilizada el [SccQueryChanges](../extensibility/sccquerychanges-function.md) operación para enumerar una colección de nombres de archivo y determina el estado de cada archivo.  
  
 El `SccQueryChanges` función tiene una lista de archivos y un puntero a la `QUERYCHANGESFUNC` devolución de llamada. El complemento de control de origen enumera sobre la lista y muestra el estado (a través de esta devolución de llamada) para cada archivo en la lista.  
  
## <a name="signature"></a>Signatura  
  
```cpp  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 pvCallerData  
 [in] El `pvCallerData` parámetro pasado por el llamador (el IDE) a [SccQueryChanges](../extensibility/sccquerychanges-function.md). El complemento de control de código fuente debe hacer ninguna suposición sobre el contenido de este valor.  
  
 pChangesData  
 [in] Puntero a un [QUERYCHANGESDATA estructura](#LinkQUERYCHANGESDATA) estructura que describe los cambios en un archivo.  
  
## <a name="return-value"></a>Valor devuelto  
 El IDE devuelve un código de error correspondiente:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Continuar el procesamiento.|  
|SCC_I_OPERATIONCANCELED|Detiene el procesamiento.|  
|SCC_E_xxx|Cualquier error de SCC correspondiente debe detener el procesamiento.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a>Estructura QUERYCHANGESDATA  
 La estructura pasada en cada archivo tiene el siguiente aspecto:  
  
```cpp  
struct QUERYCHANGESDATA_A  
{  
    DWORD  dwSize;  
    LPCSTR lpFileName;  
    DWORD  dwChangeType;  
    LPCSTR lpLatestName;  
};  
  
typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;  
  
struct QUERYCHANGESDATA_W  
{  
    DWORD   dwSize;  
    LPCWSTR lpFileName;  
    DWORD   dwChangeType;  
    LPCWSTR lpLatestName;  
};  
```  
  
 dwSize  
 Tamaño de esta estructura (en bytes).  
  
 lpFileName  
 El nombre de archivo original para este elemento.  
  
 dwChangeType  
 Código que indica el estado del archivo:  
  
|Código|Descripción|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|No se puede saber qué ha cambiado.|  
|`SCC_CHANGE_UNCHANGED`|Ningún cambio de nombre para este archivo.|  
|`SCC_CHANGE_DIFFERENT`|Archivo con una identidad diferente, pero no existe el mismo nombre en la base de datos.|  
|`SCC_CHANGE_NONEXISTENT`|Archivo no existe en la base de datos o de forma local.|  
|`SCC_CHANGE_DATABASE_DELETED`|Archivo eliminado en la base de datos.|  
|`SCC_CHANGE_LOCAL_DELETED`|Archivo eliminado localmente, pero el archivo sigue existiendo en la base de datos. Si no puede determinarse, devolver `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Archivo agregado a la base de datos, pero no existe localmente.|  
|`SCC_CHANGE_LOCAL_ADDED`|Archivo no existe en la base de datos y es un nuevo archivo local.|  
|`SCC_CHANGE_RENAMED_TO`|Archivo cambiado de nombre o en la base de datos como `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Archivo cambiado de nombre o en la base de datos de `lpLatestName`; si esto es demasiado caro realizar un seguimiento, devolver una marca diferente, como `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 El nombre de archivo actual para este elemento.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Códigos de error](../extensibility/error-codes.md)