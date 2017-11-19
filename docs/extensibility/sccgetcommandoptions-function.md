---
title: "Función SccGetCommandOptions | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetCommandOptions
helpviewer_keywords: SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6848689be19e67009314b167b60724a95fd6da5b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions (función)
Esta función pide al usuario las opciones avanzadas de un comando determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 iCommand  
 [in] El comando para el que se solicitan las opciones avanzadas (consulte [comando código](../extensibility/command-code-enumerator.md) para los valores posibles).  
  
 ppvOptions  
 [in] La estructura de opción (también puede ser `NULL`).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Correcto.|  
|SCC_I_ADV_SUPPORT|El complemento de control de origen es compatible con las opciones avanzadas para el comando.|  
|SCC_I_OPERATIONCANCELED|El usuario canceló el origen control del complemento **opciones** cuadro de diálogo.|  
|SCC_E_OPTNOTSUPPORTED|El complemento de control de código fuente no admite esta operación.|  
|SCC_E_ISCHECKEDOUT|No se puede realizar esta operación en un archivo que está desprotegido.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NONSPECIFICERROR|Error no determinado.|  
  
## <a name="remarks"></a>Comentarios  
 El IDE llama a esta función por primera vez con `ppvOptions` = `NULL` para determinar si el complemento de control de origen es compatible con la característica de opciones avanzadas para el comando especificado. Si el complemento es compatible con la característica para ese comando, el IDE llama a esta función nuevo cuando el usuario solicita opciones avanzadas (normalmente se implementa como un **avanzadas** botón en un cuadro de diálogo) y proporciona un puntero no nulo para `ppvOptions` que apunta a un `NULL` puntero. Almacena todas las opciones avanzadas especificadas por el usuario en una estructura privada y devuelve un puntero a esa estructura en el complemento `ppvOptions`. Esta estructura, a continuación, se pasa a todas las demás funciones de API de complemento de Control de origen que necesitan saber sobre él, incluidas las llamadas posteriores a la `SccGetCommandOptions` (función).  
  
 Un ejemplo puede ayudar a aclarar esta situación.  
  
 Un usuario elige el **obtener** comando y el IDE muestra un **obtener** cuadro de diálogo. Las llamadas IDE la `SccGetCommandOptions` funcionando con `iCommand` establecido en `SCC_COMMAND_GET` y `ppvOptions` establecido en `NULL`. Esto se interpreta mediante el control de código fuente complemento como la pregunta, "¿tiene las opciones avanzadas pertinentes para este comando?" Si devuelve el complemento `SCC_I_ADV_SUPPORT`, el IDE muestra un **avanzadas** botón en su **obtener** cuadro de diálogo.  
  
 La primera vez que el usuario hace clic en el **avanzadas** botón, el IDE llama de nuevo el `SccGetCommandOptions` funcione, esta vez no`NULL``ppvOptions` que apunta a un `NULL` puntero. El complemento se muestra su propio **obtener opciones de** cuadro de diálogo pide al usuario para obtener información, coloca dicha información en su propia estructura y devuelve un puntero a esa estructura en `ppvOptions`.  
  
 Si el usuario hace clic en **avanzadas** nuevo en el mismo cuadro de diálogo, el IDE llama el `SccGetCommandOptions` función sin necesidad de cambiar `ppvOptions`, de modo que la estructura se pasa al complemento. Esto permite que el complemento reinicializar el cuadro de diálogo a los valores que el usuario haya establecido anteriormente. El complemento modifica la estructura en su lugar antes de devolver.  
  
 Por último, cuando el usuario hace clic en **Aceptar** en el IDE **obtener** cuadro de diálogo, las llamadas IDE la [SccGet](../extensibility/sccget-function.md), pasando la estructura devuelta en `ppvOptions` que contiene el Opciones avanzadas.  
  
> [!NOTE]
>  El comando `SCC_COMMAND_OPTIONS` se utiliza cuando el IDE muestra un **opciones** cuadro de diálogo que permite al usuario establecer las preferencias que controlan el funcionamiento de la integración. Si desea que el complemento de control de código fuente proporcionar su propio cuadro de diálogo de preferencias, puede mostrar desde una **avanzadas** botón en el cuadro de diálogo de preferencias del IDE. El complemento es responsable únicamente de obtener y conservar esta información; el IDE no usarlo o modificarlo.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de comando](../extensibility/command-code-enumerator.md)