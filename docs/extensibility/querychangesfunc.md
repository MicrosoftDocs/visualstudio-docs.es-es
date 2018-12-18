---
title: QUERYCHANGESFUNC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 74b5241a14ebaecb05db36a9ab4e1b808917afa5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879186"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Se trata de una función de devolución de llamada utilizada por el [SccQueryChanges](../extensibility/sccquerychanges-function.md) operación para enumerar una colección de nombres de archivo y determinar el estado de cada archivo.  
  
 El `SccQueryChanges` función recibe una lista de archivos y un puntero a la `QUERYCHANGESFUNC` devolución de llamada. El complemento de control de origen enumera la lista determinada y proporciona el estado (a través de esta devolución de llamada) para cada archivo en la lista.  
  
## <a name="signature"></a>Signatura  
  
```cpp  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 pvCallerData  
 [in] El `pvCallerData` parámetro pasado por el llamador (IDE) a [SccQueryChanges](../extensibility/sccquerychanges-function.md). El complemento de control de origen debe hacer ninguna suposición sobre el contenido de este valor.  
  
 pChangesData  
 [in] Puntero a un [QUERYCHANGESDATA estructura](#LinkQUERYCHANGESDATA) estructura que describe los cambios en un archivo.  
  
## <a name="return-value"></a>Valor devuelto  
 El IDE devuelve un código de error adecuado:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Continuar el procesamiento.|  
|SCC_I_OPERATIONCANCELED|Detener el procesamiento.|  
|SCC_E_xxx|Cualquier error de SCC apropiado debería detener el procesamiento.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> Estructura QUERYCHANGESDATA  
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
 Que indica el estado del archivo de código:  
  
|Código|Descripción|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|No puede saber qué ha cambiado.|  
|`SCC_CHANGE_UNCHANGED`|Ningún cambio de nombre para este archivo.|  
|`SCC_CHANGE_DIFFERENT`|Archivo con una identidad diferente, pero no existe el mismo nombre en la base de datos.|  
|`SCC_CHANGE_NONEXISTENT`|Archivo no existe en la base de datos o localmente.|  
|`SCC_CHANGE_DATABASE_DELETED`|Archivo eliminado en la base de datos.|  
|`SCC_CHANGE_LOCAL_DELETED`|Archivo eliminado localmente, pero el archivo sigue existiendo en la base de datos. Si esto no se puede determinar, devolver `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Archivo agregado a la base de datos, pero no existe localmente.|  
|`SCC_CHANGE_LOCAL_ADDED`|Archivo no existe en la base de datos y un nuevo archivo local.|  
|`SCC_CHANGE_RENAMED_TO`|Archivo cambiado de nombre o en la base de datos como `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Archivo cambiado de nombre o en la base de datos `lpLatestName`; si esto es demasiado costosa para realizar un seguimiento, devuelve una marca diferentes, como `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 El nombre de archivo actual para este elemento.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Códigos de error](../extensibility/error-codes.md)