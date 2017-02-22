---
title: "SccRename (funci&#243;n) | Microsoft Docs"
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
  - "SccRename"
helpviewer_keywords: 
  - "SccRename (función)"
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccRename (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función cambia el nombre de un archivo en el sistema de control de código fuente.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpFileName  
 \[in\] El nombre de archivo completo del archivo que se va a cambiar el nombre.  
  
 lpNewName  
 \[in\] El nombre completo de nuevo. Si la ruta de acceso del directorio es diferente, el archivo se movió de un subdirectorio a otro.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|La operación finalizada correctamente.|  
|SCC\_E\_PROJNOTOPEN|El proyecto no está abierto en el control de código fuente.|  
|SCC\_E\_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no está autorizado para completar esta operación.|  
|SCC\_E\_COULDNOTCREATEPROJECT|No se pudo crear el proyecto como parte del proceso de cambio de nombre.|  
|SCC\_E\_OPNOTPERFORMED|No se realizó la operación.|  
|SCC\_E\_NONSPECIFICERROR|Ocurrió un error no especificado o general.|  
  
## Comentarios  
 Esta función puede utilizarse para cambiar el nombre de un archivo o moverlo de una ubicación a otra en el sistema de control de código fuente. El complemento de control de código fuente no debe intentar obtener acceso al archivo en disco. Es responsabilidad del IDE para cambiar el nombre del archivo local.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)