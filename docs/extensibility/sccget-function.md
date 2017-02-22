---
title: "SccGet (funci&#243;n) | Microsoft Docs"
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
  - "SccGet"
helpviewer_keywords: 
  - "SccGet (función)"
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGet (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función recupera una copia de uno o varios archivos para ver y compilar, pero no para edición. En la mayoría de los sistemas, los archivos se etiquetan como de solo lectura.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccGet(  
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
 \[in\] La estructura de contexto del complemento de control de origen.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 \[in\] Número de archivos especificado en el `lpFileNames` matriz.  
  
 lpFileNames  
 \[in\] Matriz de nombres completos de los archivos que desea recuperar.  
  
 Opciones  
 \[in\] Indicadores de comandos \(`SCC_GET_ALL`, `SCC_GET_RECURSIVE`\).  
  
 pvOptions  
 \[in\] Opciones específicas del complemento de control de código fuente.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Éxito de la operación get.|  
|SCC\_E\_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|  
|SCC\_E\_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|  
|SCC\_E\_FILEISCHECKEDOUT|No se puede obtener el archivo que el usuario ha desprotegido.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_NOSPECIFIEDVERSION|Especifica una versión no válida o una fecha y hora.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico; archivo no se sincronizó.|  
|SCC\_I\_OPERATIONCANCELED|Operación cancelada antes de terminar.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no está autorizado para realizar esta operación.|  
  
## Comentarios  
 Esta función se invoca con un número y una matriz de nombres de los archivos que se van a recuperar. Si el IDE pasa el indicador `SCC_GET_ALL`, esto significa que los elementos de `lpFileNames` no son archivos sino directorios y que todos los archivos bajo control de código fuente en los directorios determinados se va a recuperar.  
  
 El `SCC_GET_ALL` marca se puede combinar con la `SCC_GET_RECURSIVE` marca para recuperar todos los archivos en los directorios determinados y también todos los subdirectorios.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` nunca se debe pasar sin `SCC_GET_ALL`. Además, tenga en cuenta que si los directorios C:\\A y C:\\A\\B son pasan en una recursiva get, C:\\A\\B y todos sus subdirectorios realmente se recuperarán dos veces. Es responsabilidad del IDE, y no el origen de control del complemento, para asegurarse de que se mantengan duplicados como éste fuera de la matriz.  
  
 Por último, incluso si un origen de controlar el complemento especificado el `SCC_CAP_GET_NOUI` marca en la inicialización, lo que indica que no tiene una interfaz de usuario para un comando Get, todavía se llama a esta función por el IDE para recuperar archivos. La marca simplemente significa que el IDE no muestra un elemento de menú de Get y que el complemento no debe proporcionar ninguna interfaz de usuario.  
  
## Cambiar el nombre y SccGet  
 Situación: un usuario desprotege un archivo, por ejemplo, a.txt y lo modifica. Antes de protegerlos a.txt, un segundo usuario cambia el nombre a.txt a b.txt en la base de datos de control de código fuente, desprotege b.txt, realiza algunas modificaciones en el archivo y comprueba el archivo. El primer usuario desea que los cambios realizados por el segundo usuario, por lo que el primer usuario cambia el nombre de su versión local del archivo a.txt a b.txt y realiza una operación get en el archivo. Sin embargo, la memoria caché local que realiza un seguimiento de los números de versión aún piensa que la primera versión de a.txt se almacena localmente y por lo tanto, control de código fuente no puede resolver las diferencias.  
  
 Hay dos maneras de resolver esta situación donde la memoria caché local de versiones del control de código fuente no está sincronizada con la base de datos de control de código fuente:  
  
1.  No se permite cambiar el nombre de un archivo en la base de datos de control de código fuente que está desprotegido.  
  
2.  Realizar el equivalente de "eliminación anterior" seguido de "Agregar nuevo". El algoritmo siguiente es una manera de lograr esto.  
  
    1.  Llame a la [SccQueryChanges](../extensibility/sccquerychanges-function.md) \(función\) para obtener información sobre el cambio de nombre de a.txt a b.txt en la base de datos de control de código fuente.  
  
    2.  Cambiar el nombre de la local a.txt a b.txt.  
  
    3.  Llame a la `SccGet` función a.txt y b.txt.  
  
    4.  A.txt existe en la base de datos de control de código fuente, se purga la caché de la versión local de la información de versión a.txt que falta.  
  
    5.  B.txt desprotegido el archivo que se está combinado con el contenido del archivo local b.txt.  
  
    6.  Ahora se puede registrar el archivo b.txt actualizada.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Marcadores de bits que se utilizan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)