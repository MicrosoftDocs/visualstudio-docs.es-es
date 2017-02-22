---
title: "SccQueryInfo (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccQueryInfo"
helpviewer_keywords: 
  - "SccQueryInfo (función)"
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# SccQueryInfo (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función obtiene información de estado para un conjunto de archivos seleccionados en el control de código fuente.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 nFiles  
 \[in\] Número de archivos especificado en el `lpFileNames` matriz y la longitud de la `lpStatus` matriz.  
  
 lpFileNames  
 \[in\] Una matriz de nombres de archivos que se va a consultar.  
  
 lpStatus  
 \[entrada, salida\] Matriz en la que el complemento de control de código fuente devuelve los indicadores de estado para cada archivo. Para obtener más información, consulta [Código de estado de archivo](../extensibility/file-status-code-enumerator.md).  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Consulta fue correcta.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema con el acceso en el sistema de control de código fuente, probablemente provocado por problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_PROJNOTOPEN|El proyecto no está abierto en el control de código fuente.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico.|  
  
## Comentarios  
 Si `lpFileName` es una cadena vacía, actualmente no hay ninguna información de estado para la actualización. De lo contrario, es el nombre de ruta de acceso completa del archivo para el que puede ha cambiado la información de estado.  
  
 La matriz devuelta puede ser una máscara de bits de `SCC_STATUS_xxxx` bits. Para obtener más información, consulta [Código de estado de archivo](../extensibility/file-status-code-enumerator.md). Un sistema de control de código fuente puede no admitir todos los tipos de bits. Por ejemplo, si `SCC_STATUS_OUTOFDATE` no está disponible, pero no está establecido el bit.  
  
 Al usar esta función para desproteger archivos, tenga en cuenta lo siguiente `MSSCCI` requisitos de estado:  
  
-   `SCC_STATUS_OUTBYUSER` se establece cuando el usuario actual ha desprotegido el archivo.  
  
-   `SCC_STATUS_CHECKEDOUT` no se puede establecer a menos que `SCC_STATUS_OUTBYUSER` se establece.  
  
-   `SCC_STATUS_CHECKEDOUT` sólo se establece cuando el archivo está desprotegido en el directorio de trabajo designado.  
  
-   Si el archivo está desprotegido por el usuario actual en un directorio distinto al directorio de trabajo `SCC_STATUS_OUTBYUSER` está establecido, pero `SCC_STATUS_CHECKEDOUT` no.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)