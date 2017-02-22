---
title: "SccRemove (funci&#243;n) | Microsoft Docs"
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
  - "SccRemove"
helpviewer_keywords: 
  - "SccRemove (función)"
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccRemove (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función elimina los archivos del sistema de control de código fuente.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccRemove(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 \[in\] Número de archivos especificado en el `lpFileNames` matriz.  
  
 lpFileNames  
 \[in\] Matriz de nombres de ruta de acceso local completa de archivos que se quitarán.  
  
 lpComment  
 \[in\] El comentario que se aplicará a cada archivo que se va a quitar.  
  
 Opciones  
 \[in\] Indicadores de comando \(no utilizados\).  
  
 pvOptions  
 \[in\] Opciones específicas del complemento de control de código fuente.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Eliminación realizada correctamente.|  
|SCC\_E\_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC\_E\_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|  
|SCC\_E\_ISCHECKEDOUT|No se puede quitar un archivo porque un usuario actualmente tiene desprotegido.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico; no se quitó el archivo.|  
|SCC\_I\_OPERATIONCANCELED|Se canceló la operación antes de completarse.|  
  
## Comentarios  
 Esta función elimina los archivos del sistema de control de código fuente, pero no los elimina de la unidad de disco duro local del usuario.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)