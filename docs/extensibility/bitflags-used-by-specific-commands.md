---
title: "Marcadores de bits que se utilizan los comandos espec&#237;ficos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "marcadores de bits que se utilizan los comandos específicos de los complementos de control de código fuente"
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Marcadores de bits que se utilizan los comandos espec&#237;ficos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El comportamiento de un número de funciones de la API de complementos de Control de código fuente se puede modificar estableciendo uno o más bits en un único valor. Estos valores se conocen como marcadores de bits. Los distintos marcadores de bits utilizados por la API de complementos de Control de código fuente se detallan aquí, agrupados por la función que los utiliza.  
  
## Desprotegido marca  
 Esta marca se puede definir para el [SccAdd](../extensibility/sccadd-function.md) o [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Marcar|Valor|Descripción|  
|------------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0 x 1000|Mantener el archivo desprotegido.|  
  
## Agregar marcas  
 Estas marcas se usan por el [SccAdd](../extensibility/sccadd-function.md).  
  
|Marcar|Valor|Descripción|  
|------------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0 x 00|Se espera el complemento de control de código fuente para detectar automáticamente si el archivo es texto o binario.|  
|`SCC_FILETYPE_TEXT`|0 x 01|Tipo de archivo es texto.|  
|`SCC_FILETYPE_BINARY`|0 x 04|Tipo de archivo es binario. **Note:**  `SCC_FILETYPE_TEXT` y `SCC_FILETYPE_BINARY` marcas son mutuamente excluyentes. Establecer exactamente uno o ninguno.|  
|`SCC_ADD_STORELATEST`|0 x 02|Almacenar la última versión únicamente \(no hay diferencias\).|  
  
## Indicadores de comparación  
 El [SccDiff](../extensibility/sccdiff-function.md) estos indicadores se utilizan para definir el ámbito de una operación de comparación. La `SCC_DIFF_QD_xxx` marcas son mutuamente excluyentes. Si se especifica uno de ellos, ningún indicador visual es que se asignará. En "diff rápida" \(QD\), el complemento no determina cómo el archivo es diferente, sólo si es diferente. Si ninguna de estas marcas se especifica, que se realiza una "diff visual"; se calcula y se muestran las diferencias de archivo detallada. Si no se admite la QD solicitado, el complemento se mueve a la siguiente mejor. Por ejemplo, si el IDE solicita una suma de comprobación y el complemento no lo admite, el complemento no un contenido completo Compruebe \(aún mucho más rápido que una presentación visual\).  
  
|Marcar|Valor|Descripción|  
|------------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0 x 0002|Ignorar las diferencias de mayúsculas.|  
|`SCC_DIFF_IGNORESPACE`|0 x 0004|Omitir las diferencias de espacios en blanco. **Note:**  El `SCC_DIFF_IGNORECASE` y `SCC_DIFF_IGNORESPACE` marcas son marcadores de bits opcional.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD comparando el contenido completo del archivo.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD por la suma de comprobación.|  
|`SCC_DIFF_QD_TIME`|0x0040|QD con la marca de fecha y hora de archivo.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Se trata de una máscara que se utiliza para comprobar los marcadores de bits QD. No se debe pasar a una función; los tres marcadores de bits QD son mutuamente excluyentes. QD siempre no significa mostrar ninguna interfaz de usuario.|  
  
## Marca de PopulateList  
 Esta marca se usa por el [SccPopulateList](../extensibility/sccpopulatelist-function.md) en el `fOptions` parámetro.  
  
|Marcar|Valor|Descripción|  
|------------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|El IDE está pasando directorios, no archivos.|  
  
## Marcas de PopulateDirList  
 Estas marcas se usan por el [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) en el `fOptions` parámetro.  
  
|Valor de opción|Valor|Descripción|  
|---------------------|-----------|-----------------|  
|SCC\_PDL\_ONELEVEL|0x0000|Examinar sólo un nivel de directorios para directorios \(es decir, el valor predeterminado\).|  
|SCC\_PDL\_RECURSIVE|0 x 0001|Recursivamente examine todos los directorios en cada directorio dado.|  
|SCC\_PDL\_INCLUDEFILES|0 x 0002|Incluir nombres de archivo en el proceso de examen.|  
  
## Marcas de OpenProject  
 Estas marcas se usan por el [SccOpenProject](../extensibility/sccopenproject-function.md) en el `dwFlags` parámetro.  
  
|Valor de opción|Valor|Descripción|  
|---------------------|-----------|-----------------|  
|SCC\_OP\_CREATEIFNEW|0x00000001L|Si el proyecto no existe en el control de código fuente, créelo. Si no se establece este indicador, solicite el usuario para el proyecto que cree \(a menos que `SCC_OP_SILENTOPEN` se especifica la marca\).|  
|SCC\_OP\_SILENTOPEN|0x00000002L|No preguntar al usuario crear un proyecto. valor devuelto `SCC_E_UNKNOWNPROJECT`.|  
  
## Obtener indicadores  
 Estas marcas se usan por el [SccGet](../extensibility/sccget-function.md) y [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Marcar|Valor|Descripción|  
|------------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|El IDE está pasando directorios, no archivos: obtener todos los archivos en estos directorios.|  
|`SCC_GET_RECURSIVE`|0x00000002L|El IDE está pasando directorios: obtener estos directorios y todos sus subdirectorios.|  
  
## Valores de nOption  
 Estas marcas se usan por el [SccSetOption](../extensibility/sccsetoption-function.md) en el `nOption` parámetro.  
  
|Marcar|Valor|Descripción|  
|------------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Establecer estado de la cola de eventos.|  
|`SCC_OPT_USERDATA`|0x00000002L|Especificar los datos de usuario para `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|El IDE puede controlar la cancelación|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Establece una devolución de llamada para los cambios de nombre.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Deshabilitar la desprotección de interfaz de usuario del complemento de control de origen y no se establece el directorio de trabajo.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Agregar desde el sistema de control de código fuente para especificar un directorio de trabajo. Intente compartir en el proyecto asociado si es un descendiente directo.|  
  
## dwVal marcadores de bits  
 Estas marcas se usan por el [SccSetOption](../extensibility/sccsetoption-function.md) en el `dwVal` parámetro.  
  
|Marcar|Valor|Descripción|Utilizado por `nOption` valor|  
|------------|-----------|-----------------|-----------------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Suspende la actividad de la cola de eventos.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Habilita el registro de cola de eventos.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|\(Valor predeterminado\) No tiene ningún modo de cancelar; debe proporcionar complemento si lo desea.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|IDE controla la cancelación.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|\(Valor predeterminado\) Aceptar para desproteger desde la interfaz de usuario de complemento; se establece el directorio de trabajo.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|Ningún complemento desprotección de interfaz de usuario, no hay directorio de trabajo.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)