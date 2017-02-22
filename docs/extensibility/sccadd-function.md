---
title: "SccAdd (funci&#243;n) | Microsoft Docs"
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
  - "SccAdd"
helpviewer_keywords: 
  - "SccAdd (función)"
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# SccAdd (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función agrega nuevos archivos al sistema de control de código fuente.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 \[in\] Número de archivos seleccionados para agregar al proyecto actual, como se indica en la `lpFileNames` matriz.  
  
 lpFileNames  
 \[in\] Matriz de nombres locales completos de archivos que se va a agregar.  
  
 lpComment  
 \[in\] El comentario que se aplicará a todos los archivos que se va a agregar.  
  
 pfOptions  
 \[in\] Matriz de indicadores de comando, proporcionado por el archivo.  
  
 pvOptions  
 \[in\] Opciones específicas del complemento de control de código fuente.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|La operación de agregar fue correcta.|  
|SCC\_E\_FILEALREADYEXISTS|El archivo seleccionado ya está bajo control de código fuente.|  
|SCC\_E\_TYPENOTSUPPORTED|El tipo de archivo \(por ejemplo, binario\) no es compatible con el sistema de control de código fuente.|  
|SCC\_E\_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico; Agregue no realiza.|  
|SCC\_I\_OPERATIONCANCELED|Se canceló la operación antes de completarse.|  
|SCC\_I\_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
|SCC\_E\_FILENOTEXIST|No se encontró el archivo local.|  
  
## Comentarios  
 La habitual `fOptions` se reemplazan aquí por una matriz `pfOptions`, con una `LONG` opción especificación por archivo. Esto es porque el tipo de archivo puede variar de un archivo a.  
  
> [!NOTE]
>  No es válido especificar ambos `SCC_FILETYPE_TEXT` y `SCC_FILETYPE_BINARY` Opciones para el mismo archivo, pero es válido especificar ninguno. Configuración no es lo mismo que establecer `SCC_FILETYPE_AUTO`, en cuyo caso el origen de controlar el complemento detecta automáticamente el tipo de archivo.  
  
 A continuación se muestra la lista de marcas que se usan en el `pfOptions` matriz:  
  
|Opción|Valor|Significado|  
|------------|-----------|-----------------|  
|SCC\_FILETYPE\_AUTO|0 x 00|El complemento de control de código fuente debe detectar el tipo de archivo.|  
|SCC\_FILETYPE\_TEXT|0 x 01|Indica un archivo de texto ASCII.|  
|SCC\_FILETYPE\_BINARY|0 x 02|Indica un tipo de archivo que no sea de texto ASCII.|  
|SCC\_ADD\_STORELATEST|0 x 04|Almacena sólo la copia más reciente del archivo, no hay diferencias.|  
|SCC\_FILETYPE\_TEXT\_ANSI|0 x 08|Trata el archivo como texto ANSI.|  
|SCC\_FILETYPE\_UTF8|0 x 10|Trata el archivo como texto Unicode en formato UTF8.|  
|SCC\_FILETYPE\_UTF16LE|0 x 20|Trata el archivo como texto Unicode en UTF16 Little Endian formato.|  
|SCC\_FILETYPE\_UTF16BE|0 x 40|Trata el archivo como texto Unicode en UTF16 Big Endian de formato.|  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)