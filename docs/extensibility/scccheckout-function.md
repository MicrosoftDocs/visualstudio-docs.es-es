---
title: "SccCheckout (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCheckout"
helpviewer_keywords: 
  - "SccCheckout (función)"
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccCheckout (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dada una lista de nombres de archivo completo, esta función desprotege ellos en la unidad local. El comentario se aplica a todos los archivos que se desprotegen. El argumento comentario puede ser un `null` cadena.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccCheckout (  
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
 \[in\] Número de archivos seleccionados estén desprotegidos.  
  
 lpFileNames  
 \[in\] Matriz de nombres de ruta de acceso local completa de los archivos estén desprotegidos.  
  
 lpComment  
 \[in\] Comentario que se aplicará a cada uno de los archivos seleccionados que se está desprotegidos.  
  
 Opciones  
 \[in\] Indicadores de comandos \(consulte [Marcadores de bits que se utilizan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)\).  
  
 pvOptions  
 \[in\] Opciones específicas del complemento de control de código fuente.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Desprotección fue correcta.|  
|SCC\_E\_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico. No se ha desprotegido el archivo.|  
|SCC\_E\_ALREADYCHECKEDOUT|El usuario ya tiene desprotegido el archivo.|  
|SCC\_E\_FILEISLOCKED|El archivo está bloqueado, lo que prohíbe la creación de nuevas versiones.|  
|SCC\_E\_FILEOUTEXCLUSIVE|Otro usuario ha hecho una desprotección exclusiva en este archivo.|  
|SCC\_I\_OPERATIONCANCELED|Se canceló la operación antes de completarse.|  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Marcadores de bits que se utilizan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)