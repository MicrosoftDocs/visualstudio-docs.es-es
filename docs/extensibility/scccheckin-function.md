---
title: "SccCheckin (funci&#243;n) | Microsoft Docs"
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
  - "SccCheckin"
helpviewer_keywords: 
  - "SccCheckin (función)"
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# SccCheckin (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función comprueba en archivos previamente desprotegido en el sistema de control de código fuente almacena los cambios y la creación de una nueva versión. Esta función se invoca con un número y una matriz de nombres de los archivos para protegerse.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 \[in\] Número de archivos seleccionados para protegerse.  
  
 lpFileNames  
 \[in\] Matriz de nombres de ruta de acceso local completa de archivos que se va a proteger.  
  
 lpComment  
 \[in\] Comentario que se aplicará a cada uno de los archivos seleccionados que se protege. Esto es `NULL` Si el complemento de control de código fuente debe solicitar un comentario.  
  
 Opciones  
 \[in\] Indicadores de comando, 0 o `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 \[in\] Opciones específicas del complemento de control de código fuente.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Los archivos se ha protegido correctamente.|  
|SCC\_E\_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico. El archivo no se ha protegido.|  
|SCC\_E\_NOTCHECKEDOUT|El usuario no ha desprotegido el archivo, por lo que no puede protegerlo.|  
|SCC\_E\_CHECKINCONFLICT|No se pudo realizar la protección porque:<br /><br /> -   Otro usuario ha protegido con antelación y `bAutoReconcile` fuese falsa.<br /><br /> O bien<br /><br /> -   No se puede realizar la combinación automática \(por ejemplo, cuando los archivos son binarios\).|  
|SCC\_E\_VERIFYMERGE|Archivo ha sido combinado automáticamente pero no se ha protegido espera de comprobación del usuario.|  
|SCC\_E\_FIXMERGE|Archivo ha sido combinan automáticamente, pero no se han protegido debido a un conflicto de combinación que debe resolverse manualmente.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC\_I\_OPERATIONCANCELED|Se canceló la operación antes de completarse.|  
|SCC\_I\_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
|SCC\_E\_FILENOTEXIST|No se encontró el archivo local.|  
  
## Comentarios  
 El comentario se aplica a todos los archivos que se protege. El argumento comentario puede ser un `null` de cadena, en cuyo caso el complemento de control de código fuente puede pedir al usuario una cadena de comentario para cada archivo.  
  
 El `fOptions` argumento puede asignar un valor de la `SCC_KEEP_CHECKEDOUT` marca para indicar que la intención del usuario para proteger el archivo y compruébelo de nuevo.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)