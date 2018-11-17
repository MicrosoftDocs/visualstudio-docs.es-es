---
title: SccDirDiff (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d2c45773a9d45c69cfed4f773bc5cdfcfa1c305
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791194"
---
# <a name="sccdirdiff-function"></a>SccDirDiff (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función muestra las diferencias entre el directorio local actual en el disco de cliente y el proyecto bajo control de código fuente correspondiente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in] La estructura de contexto de complemento de control de origen.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.  
  
 lpDirName  
 [in] Ruta de acceso completa al directorio local para que se va a mostrar una diferencia visual.  
  
 dwFlags  
 [in] Marcas de comando (vea la sección Comentarios sección).  
  
 pvOptions  
 [in] Opciones de específicas del complemento de control de código fuente.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|El directorio en el disco es el mismo que el proyecto en el control de código fuente.|  
|SCC_I_FILESDIFFER|El directorio en el disco es diferente al proyecto de control de código fuente.|  
|SCC_I_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
|SCC_E_FILENOTCONTROLLED|El directorio no está bajo control de código fuente.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no específico.|  
|SCC_E_FILENOTEXIST|No se encontró el directorio local.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función se utiliza para indicar el control de código fuente para mostrar al usuario una lista de los cambios realizados en un directorio especificado. El complemento, su propia ventana, abre en un formato de su elección, para mostrar las diferencias entre el directorio del usuario en el disco y el proyecto bajo control de versiones correspondiente.  
  
 Si el complemento admite ver una comparación de directorios en absoluto, debe admitir la comparación de directorios según el nombre de archivo incluso si no se admiten las opciones de "comparación de rápida".  
  
|`dwFlags`|Interpretación|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Comparación entre mayúsculas y minúsculas (se puede usar para la comparación rápida o visual).|  
|SCC_DIFF_IGNORESPACE|Omite los espacios en blanco (se puede usar para rápido diff u objeto visual).|  
|SCC_DIFF_QD_CONTENTS|Si se admite el complemento de control de código fuente, en modo silencioso compara el directorio, byte a byte.|  
|SCC_DIFF_QD_CHECKSUM|Si compatibles con el complemento, en modo silencioso compara el directorio a través de una suma de comprobación o, si no se admite, recurre a SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Si compatibles con el complemento, en modo silencioso compara el directorio a través de su marca de tiempo o, si no se admite, recurre a SCC_DIFF_QD_CHECKSUM o SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
>  Esta función utiliza los mismos marcadores de comando como el [SccDiff](../extensibility/sccdiff-function.md). Sin embargo, puede elegir un complemento de control de origen no admite la operación de "diff-rápido" para los directorios.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)

