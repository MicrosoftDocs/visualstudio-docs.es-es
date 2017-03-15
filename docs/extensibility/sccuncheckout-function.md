---
title: "SccUncheckout (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUncheckout"
helpviewer_keywords: 
  - "SccUncheckout (función)"
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccUncheckout (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función deshace una operación de desprotección anterior, con lo que se restaura el contenido del archivo seleccionado o los archivos al estado anterior a la desprotección. Se perderán todos los cambios realizados en el archivo desde la desprotección.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
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
 \[in\] Matriz de nombres de ruta de acceso local completa de archivos para el que se va a deshacer una desprotección.  
  
 Opciones  
 \[in\] Indicadores de comando \(no utilizados\).  
  
 pvOptions  
 \[in\] Opciones específicas del complemento de control de código fuente.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Deshacer desprotección fue correcta.|  
|SCC\_E\_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico. Deshacer desprotección no se realizó correctamente.|  
|SCC\_E\_NOTCHECKEDOUT|El usuario no tiene el archivo desprotegido.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC\_E\_PROJNOTOPEN|No se abrió el proyecto de control de código fuente.|  
|SCC\_I\_OPERATIONCANCELED|Se canceló la operación antes de completarse.|  
  
## Comentarios  
 Después de esta operación, el `SCC_STATUS_CHECKEDOUT` y `SCC_STATUS_MODIFIED` marcas ambos se borrará de los archivos en el que se realizó la desprotección.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)