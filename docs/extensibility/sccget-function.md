---
title: "Función SccGet | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGet
helpviewer_keywords: SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20abad6a195d8493be8849588b86035d03fdc654
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="sccget-function"></a>SccGet (función)
Esta función recupera una copia de uno o más archivos para ver y compilar pero no para su edición. En la mayoría de los sistemas, los archivos se etiquetan como de solo lectura.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto del complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 [in] Número de archivos especificado en el `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Matriz de nombres completos de los archivos que desea recuperar.  
  
 fOptions  
 [in] Indicadores de comandos (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Opciones de específicas del complemento de control de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Éxito de la operación get.|  
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|  
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|  
|SCC_E_FILEISCHECKEDOUT|No se puede obtener el archivo que el usuario ha desprotegido actualmente.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NOSPECIFIEDVERSION|Especificar una versión no válida o la fecha y hora.|  
|SCC_E_NONSPECIFICERROR|Error no determinado; archivo no se sincronizó.|  
|SCC_I_OPERATIONCANCELED|Operación cancelada antes de la finalización.|  
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para realizar esta operación.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función se invoca con un recuento y una matriz de nombres de los archivos que se van a recuperar. Si el IDE pasa la marca `SCC_GET_ALL`, esto significa que los elementos de `lpFileNames` no son archivos sino directorios, y que todos los archivos bajo control de código fuente en los directorios determinados se van a recuperar.  
  
 El `SCC_GET_ALL` marca puede combinarse con la `SCC_GET_RECURSIVE` marca para recuperar todos los archivos en los directorios determinados y también todos los subdirectorios.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE`nunca se debe pasar sin `SCC_GET_ALL`. Además, tenga en cuenta que si directorios C:\A y C:\A\B son ambos se pasan en una recursiva obtener, C:\A\B y todos sus subdirectorios realmente se recuperarán dos veces. Es responsabilidad del IDE, y no el origen de control del complemento, para asegurarse de que se mantengan duplicados como éste fuera de la matriz.  
  
 Por último, incluso si un origen de controlar el complemento especificado el `SCC_CAP_GET_NOUI` marca en la inicialización, lo que indica que no tiene una interfaz de usuario para un comando Get, todavía puede llamar a esta función mediante el IDE para recuperar archivos. La marca simplemente quiere decir que el IDE no muestra un elemento de menú de Get y que el complemento no necesite proporcionar cualquier interfaz de usuario.  
  
## <a name="renaming-and-sccget"></a>Cambiar el nombre y SccGet  
 Situación: un usuario desprotege un archivo, por ejemplo, a.txt y lo modifique. Antes de protegerlos a.txt, un segundo usuario cambia el nombre a.txt b.txt en la base de datos de control de código fuente, desprotege b.txt, realiza algunas modificaciones en el archivo y vuelve a proteger el archivo. El primer usuario quiere que los cambios realizados por el segundo usuario, por lo que el primer usuario cambia el nombre de su versión local del archivo a.txt a b.txt y realiza una operación get en el archivo. No obstante, la memoria caché local que realiza un seguimiento de los números de versión aún considera la primera versión de a.txt se almacena localmente y por lo tanto, control de código fuente no puede resolver las diferencias.  
  
 Hay dos maneras de resolver esta situación donde la memoria caché local de versiones del control de código fuente no está sincronizada con la base de datos de control de código fuente:  
  
1.  No se permite cambiar el nombre de un archivo en la base de datos de control de código fuente que está desprotegido.  
  
2.  Es el equivalente de "eliminación anterior" seguido de "Agregar nuevo". El algoritmo siguiente es una manera de lograr esto.  
  
    1.  Llame a la [SccQueryChanges](../extensibility/sccquerychanges-function.md) función para obtener información sobre el cambio de nombre de a.txt a b.txt en la base de datos de control de código fuente.  
  
    2.  Cambiar el nombre de la a.txt local a b.txt.  
  
    3.  Llame a la `SccGet` función para a.txt y b.txt.  
  
    4.  Porque a.txt no existe en la base de datos de control de código fuente, la memoria caché local de versiones se purga de la información de versión a.txt que falta.  
  
    5.  El archivo b.txt desprotección se combina con el contenido del archivo b.txt local.  
  
    6.  Ahora se puede comprobar el archivo actualizado b.txt.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)