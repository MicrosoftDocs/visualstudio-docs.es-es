---
title: "Función SccDirDiff | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccDirDiff
helpviewer_keywords: SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c1f6f990bb33ddbc1d7591fa3ab9837f472f8418
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="sccdirdiff-function"></a>SccDirDiff (función)
Esta función muestra las diferencias entre el directorio local actual en el disco de cliente y el proyecto bajo control de código fuente correspondiente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpDirName  
 [in] Ruta de acceso completa al directorio local para el que se muestran una diferencia visual.  
  
 dwFlags  
 [in] Indicadores de comandos (vea la sección Comentarios sección).  
  
 pvOptions  
 [in] Opciones de específicas del complemento de control de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|El directorio en el disco es el mismo que el proyecto de control de código fuente.|  
|SCC_I_FILESDIFFER|El directorio en el disco es diferente al proyecto de control de código fuente.|  
|SCC_I_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
|SCC_E_FILENOTCONTROLLED|El directorio no está bajo control de código fuente.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no determinado.|  
|SCC_E_FILENOTEXIST|No se pudo encontrar el directorio local.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función se utiliza para indicar el control de código fuente complemento para mostrar al usuario una lista de los cambios en un directorio especificado. El complemento, su propia ventana, abre en un formato de su elección, para mostrar las diferencias entre el directorio del usuario en el disco y el proyecto bajo control de versiones correspondiente.  
  
 Si una comparación de complemento admite de directorios en absoluto, debe admitir la comparación de directorios según el nombre de archivo incluso si no se admiten las opciones de "rápidas diff".  
  
|`dwFlags`|Interpretación|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Comparación entre mayúsculas y minúsculas (se puede usar para una comparación rápida o visual).|  
|SCC_DIFF_IGNORESPACE|Omite los espacios en blanco (se puede usar para la comparación rápida o visual).|  
|SCC_DIFF_QD_CONTENTS|Si admite el complemento de control de código fuente, en modo silencioso compara el directorio, byte a byte.|  
|SCC_DIFF_QD_CHECKSUM|Si admite complemento, en modo silencioso compara el directorio a través de una suma de comprobación o, si no se admite, vuelve a SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Si admite complemento, en modo silencioso compara el directorio a través de su marca de tiempo o, si no se admite, recurre en SCC_DIFF_QD_CHECKSUM o SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
>  Esta función utiliza los mismos marcadores de comando como el [SccDiff](../extensibility/sccdiff-function.md). Sin embargo, puede elegir un complemento de control de código fuente que no admita la operación de "rápidas diff" para los directorios.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)