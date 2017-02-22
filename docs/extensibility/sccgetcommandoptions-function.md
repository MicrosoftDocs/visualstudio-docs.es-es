---
title: "SccGetCommandOptions (funci&#243;n) | Microsoft Docs"
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
  - "SccGetCommandOptions"
helpviewer_keywords: 
  - "SccGetCommandOptions (función)"
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetCommandOptions (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función pide al usuario opciones avanzadas para un comando determinado.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 iCommand  
 \[in\] El comando para el que se solicitan opciones avanzadas \(consulte [Código de comando](../extensibility/command-code-enumerator.md) posibles valores\).  
  
 ppvOptions  
 \[in\] La estructura de opción \(también puede ser `NULL`\).  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Correcto.|  
|SCC\_I\_ADV\_SUPPORT|El complemento de control de código fuente admite opciones avanzadas para el comando.|  
|SCC\_I\_OPERATIONCANCELED|El usuario canceló el origen control del complemento **opciones** cuadro de diálogo.|  
|SCC\_E\_OPTNOTSUPPORTED|El complemento de control de código fuente no admite esta operación.|  
|SCC\_E\_ISCHECKEDOUT|No se puede realizar esta operación en un archivo que está desprotegido.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico.|  
  
## Comentarios  
 El IDE llama a esta función por primera vez con `ppvOptions`\=`NULL` para determinar si el complemento de control de código fuente admite la característica de opciones avanzadas para el comando especificado. Si el complemento admite la característica de ese comando, el IDE llama a esta función nuevo cuando el usuario solicita opciones avanzadas \(normalmente se implementa como un **avanzadas** botón en un cuadro de diálogo\) y proporciona un puntero no NULL para `ppvOptions` que apunta a un `NULL` puntero. El complemento almacena todas las opciones avanzadas especificadas por el usuario en una estructura private y devuelve un puntero a esa estructura en `ppvOptions`. Esta estructura se pasa a todas las demás funciones de la API de complementos de Control de código fuente que necesitan saber sobre él, incluidas las llamadas posteriores a la `SccGetCommandOptions` \(función\).  
  
 Un ejemplo puede ayudar a clarificar esta situación.  
  
 Un usuario elige el **obtener** comando y el IDE muestra un **obtener** cuadro de diálogo. Las llamadas IDE la `SccGetCommandOptions` funciona con `iCommand` establecido en `SCC_COMMAND_GET` y `ppvOptions` establecido en `NULL`. Esto se interpreta mediante el control de código fuente como la pregunta, "¿tiene las opciones avanzadas de este comando?" Si el complemento devuelve `SCC_I_ADV_SUPPORT`, el IDE muestra un **avanzadas** botón en su **obtener** cuadro de diálogo.  
  
 La primera vez que el usuario hace clic en el **avanzadas** botón, el IDE llama de nuevo el `SccGetCommandOptions` funcione, esta vez no`NULL` `ppvOptions` que apunta a un `NULL` puntero.  El complemento se muestra su propia **obtener opciones** cuadro de diálogo pide al usuario información, coloca esa información en su propia estructura y devuelve un puntero a esa estructura en `ppvOptions`.  
  
 Si el usuario hace clic **avanzadas** en el mismo cuadro de diálogo, el IDE llama de nuevo el `SccGetCommandOptions` función nuevo sin cambiar `ppvOptions`, de modo que la estructura se pasa al complemento. Esto permite que el complemento reinicializar el cuadro de diálogo a los valores que el usuario haya establecido anteriormente. El complemento modifica la estructura en su lugar antes de devolver.  
  
 Por último, cuando el usuario hace clic en **Aceptar** en el IDE **obtener** cuadro de diálogo, las llamadas IDE la [SccGet](../extensibility/sccget-function.md), pasando la estructura devuelta en `ppvOptions` que contiene las opciones avanzadas.  
  
> [!NOTE]
>  El comando `SCC_COMMAND_OPTIONS` se usa cuando el IDE muestra un **opciones** cuadro de diálogo que permite al usuario establece las preferencias que controlan el funcionamiento de la integración. Si desea que el complemento de control de código fuente proporcionar su propio cuadro de diálogo Preferencias, puede mostrar desde una **avanzadas** botón en el cuadro de diálogo de preferencias del IDE. El complemento es exclusivamente responsable de obtener y almacenar esta información; el IDE no utilizarla ni modificarlo.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de comando](../extensibility/command-code-enumerator.md)