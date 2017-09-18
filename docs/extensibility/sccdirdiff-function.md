---
title: "SccDirDiff (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDirDiff"
helpviewer_keywords: 
  - "SccDirDiff (función)"
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccDirDiff (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función muestra las diferencias entre el directorio local actual en el disco de cliente y el proyecto bajo control de código fuente correspondiente.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parámetros  
 pContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpDirName  
 \[in\] Ruta de acceso completa al directorio local para el que se muestran una diferencia visual.  
  
 dwFlags  
 \[in\] Indicadores de comandos \(vea la sección Comentarios sección\).  
  
 pvOptions  
 \[in\] Opciones específicas del complemento de control de código fuente.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|El directorio en el disco es el mismo que el proyecto en control de código fuente.|  
|SCC\_I\_FILESDIFFER|El directorio en el disco es diferente al proyecto en control de código fuente.|  
|SCC\_I\_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
|SCC\_E\_FILENOTCONTROLLED|El directorio no está bajo control de código fuente.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Error no específico.|  
|SCC\_E\_FILENOTEXIST|No se encontró el directorio local.|  
  
## Comentarios  
 Esta función se utiliza para indicar el control de código fuente para mostrar al usuario una lista de los cambios en un directorio especificado. El complemento abre su propia ventana, en un formato de su elección, para mostrar las diferencias entre el directorio del usuario en el disco y el proyecto bajo control de versiones correspondiente.  
  
 Si una comparación de complemento admite de directorios en absoluto, debe admitir la comparación de directorios según el nombre de archivo incluso si no se admiten las opciones "quick diff".  
  
|`dwFlags`|Interpretación|  
|---------------|--------------------|  
|SCC\_DIFF\_IGNORECASE|Comparación entre mayúsculas y minúsculas \(se puede usar para la comparación rápida o visual\).|  
|SCC\_DIFF\_IGNORESPACE|Omite los espacios en blanco \(se puede usar para la comparación rápida o visual\).|  
|SCC\_DIFF\_QD\_CONTENTS|Si se admite el complemento de control de código fuente, en modo silencioso compara el directorio, byte a byte.|  
|SCC\_DIFF\_QD\_CHECKSUM|Si admite Plug\-in, silenciosamente compara el directorio a través de una suma de comprobación o, si no se admite, vuelve a SCC\_DIFF\_QD\_CONTENTS.|  
|SCC\_DIFF\_QD\_TIME|Si admite Plug\-in, silenciosamente compara el directorio a través de su marca de tiempo o, si no se admite, vuelve a SCC\_DIFF\_QD\_CHECKSUM o SCC\_DIFF\_QD\_CONTENTS.|  
  
> [!NOTE]
>  Esta función utiliza los mismos marcadores de comando como el [SccDiff](../extensibility/sccdiff-function.md). Sin embargo, puede elegir un complemento de control de código fuente no admite la operación de "quick diff" para directorios.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)