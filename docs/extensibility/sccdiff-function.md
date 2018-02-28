---
title: "Función SccDiff | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 832d80c3ca49cc03c4a66b6a4cf931dd40686c82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="sccdiff-function"></a>SccDiff (función)
Esta función muestra (o simplemente, opcionalmente, busca) las diferencias entre el archivo actual (en el disco local) y su última versión de archivo protegido en el origen de sistema de control.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpFileName  
 [in] Nombre de archivo para el que se solicita la diferencia.  
  
 fOptions  
 [in] Marcas de comando. Para obtener más información, vea la sección Comentarios.  
  
 pvOptions  
 [in] Opciones de específicas del complemento de control de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|La versión de servidor y de copia de trabajo son idénticos.|  
|SCC_I_FILESDIFFERS|La copia de trabajo difiere de la versión bajo control de código fuente.|  
|SCC_I_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NONSPECIFICERROR|Error no determinado; no se ha obtenido la diferencia de archivo.|  
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función tiene dos propósitos diferentes. De forma predeterminada, muestra una lista de cambios en un archivo. El complemento de control de código fuente abre su propia ventana, en el mismo formato que elija, para mostrar las diferencias entre el archivo del usuario en el disco y la versión más reciente del archivo bajo control de código fuente.  
  
 Como alternativa, el IDE simplemente que necesite determinar si un archivo ha cambiado. Por ejemplo, el IDE necesite determinar si es seguro desproteger un archivo sin informar al usuario. En ese caso, el IDE se pasa en el `SCC_DIFF_CONTENTS` marca. El complemento de control de origen debe comprobar el archivo en disco, byte a byte, con el archivo controlado por código fuente y devolver un valor que indica si los dos archivos son diferentes sin mostrar nada al usuario.  
  
 Como una optimización del rendimiento, el complemento de control de código fuente puede usar una alternativa basada en una suma de comprobación o una marca de tiempo en lugar de la comparación byte a byte que se llama para `SCC_DIFF_CONTENTS`: estas formas de comparación son obviamente más rápido pero menos confiable. No todos los sistemas de control de código fuente pueden admitir estos métodos de comparación alternativo, y el complemento podría tener que recurrir a una comparación de contenido. Todos los complementos código fuente control deben, como mínimo, admitir una comparación de contenido.  
  
> [!NOTE]
>  Las marcas de diferencia rápida son mutuamente excluyentes. Es válido para pasar no existen marcadores, pero no es válido para pasar al mismo tiempo más de uno. `SCC_DIFF_QUICK_DIFF`, que es una máscara que combina todas las marcas se pueden utilizar para probar, pero nunca se debe pasar como parámetro.  
  
|`fOption`|Significado|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|Comparación entre mayúsculas y minúsculas (se puede usar para diferencia rápido o visual).|  
|SCC_DIFF_IGNORESPACE|Omite los espacios en blanco (puede utilizarse para diferencia rápido o visual).|  
|SCC_DIFF_QD_CONTENTS|En modo silencioso compara el archivo, byte a byte.|  
|SCC_DIFF_QD_CHECKSUM|En modo silencioso compara el archivo a través de una suma de comprobación cuando se admita. Si no se admite, vuelve a obtener una comparación de contenido.|  
|SCC_DIFF_QD_TIME|En modo silencioso compara el archivo a través de su marca de tiempo cuando se admita. Si no se admite, vuelve a obtener una comparación de contenido.|  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)