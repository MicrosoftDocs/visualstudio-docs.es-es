---
title: Marcadores de bits utilizados por comandos específicos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43dc083812bc172fe4a9f80335742b3faab2e1f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184694"
---
# <a name="bitflags-used-by-specific-commands"></a>Marcas de bits usadas por comandos específicos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El comportamiento de una serie de funciones en la API de complemento de Control de código fuente puede modificarse estableciendo uno o más bits en un solo valor. Estos valores se conocen como marcadores de bits. Los marcadores de bits distintos usando la API de complemento de Control de código fuente se detallan en este caso, agrupados por la función que los usa.  
  
## <a name="checked-out-flag"></a>Desprotegido marca  
 Este indicador puede establecerse para cualquier el [SccAdd](../extensibility/sccadd-function.md) o [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Marcar|Valor|DESCRIPCIÓN|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|Mantener el archivo desprotegido.|  
  
## <a name="add-flags"></a>Agregue marcadores  
 Estas marcas se usan por el [SccAdd](../extensibility/sccadd-function.md).  
  
|Marcar|Valor|DESCRIPCIÓN|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|Se espera el complemento de control de código fuente para detectar automáticamente si el archivo es texto o binario.|  
|`SCC_FILETYPE_TEXT`|0x01|Tipo de archivo es texto.|  
|`SCC_FILETYPE_BINARY`|0x04|Tipo de archivo es binario. **Nota:** `SCC_FILETYPE_TEXT` y `SCC_FILETYPE_BINARY` marcas son mutuamente excluyentes. Establecer exactamente uno o ninguno.|  
|`SCC_ADD_STORELATEST`|0x02|Store solo la última versión (no hay diferencias).|  
  
## <a name="diff-flags"></a>Marcas de comparación  
 El [SccDiff](../extensibility/sccdiff-function.md) estas marcas se utiliza para definir el ámbito de una operación de comparación. El `SCC_DIFF_QD_xxx` marcas son mutuamente excluyentes. Si se especifica uno de ellos, no hay comentarios visuales son que se asignará. En "diff rápido" (PC), el complemento no determina cómo el archivo es diferente, sólo si es diferente. Si ninguna de estas marcas se especifica, que se realiza una "diferencia visual"; se calcula y se muestran las diferencias de archivo detallada. Si no se admite el PC solicitado, el complemento se mueve a la siguiente mejor. Por ejemplo, si el IDE solicita una suma de comprobación y el complemento no lo admite, el complemento no un contenido completo Compruebe (todavía mucho más rápido que una presentación visual).  
  
|Marcar|Valor|DESCRIPCIÓN|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|Omitir las diferencias de caja.|  
|`SCC_DIFF_IGNORESPACE`|0x0004|Omitir las diferencias de espacio en blanco. **Nota:**  El `SCC_DIFF_IGNORECASE` y `SCC_DIFF_IGNORESPACE` marcas son marcadores de bits opcional.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD comparando el contenido completo del archivo.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|PC mediante la suma de comprobación.|  
|`SCC_DIFF_QD_TIME`|0x0040|PC con la marca de fecha y hora de archivo.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Se trata de una máscara que se utiliza para comprobar todos los marcadores de bits de PC. No debe pasarse a una función; los tres marcadores de bits de PC son mutuamente excluyentes. QD siempre no significa mostrar ninguna interfaz de usuario.|  
  
## <a name="populatelist-flag"></a>Marca PopulateList  
 Esta marca se usa por la [SccPopulateList](../extensibility/sccpopulatelist-function.md) en el `fOptions` parámetro.  
  
|Marcar|Valor|DESCRIPCIÓN|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|El IDE está pasando los directorios, no archivos.|  
  
## <a name="populatedirlist-flags"></a>Marcas de PopulateDirList  
 Estas marcas se usan por el [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) en el `fOptions` parámetro.  
  
|Valor de opción|Value|DESCRIPCIÓN|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Examinar solo un nivel de directorios para los directorios (es decir, el valor predeterminado).|  
|SCC_PDL_RECURSIVE|0x0001|Recursivamente examine todos los directorios en cada directorio determinado.|  
|SCC_PDL_INCLUDEFILES|0x0002|Incluir nombres de archivo en el proceso de examen.|  
  
## <a name="openproject-flags"></a>Marcas de OpenProject  
 Estas marcas se usan por el [SccOpenProject](../extensibility/sccopenproject-function.md) en el `dwFlags` parámetro.  
  
|Valor de opción|Value|DESCRIPCIÓN|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Si el proyecto no existe en el control de código fuente, créela. Si no se establece esta marca, solicite el usuario para el proyecto que cree (a menos que `SCC_OP_SILENTOPEN` indicador se especifica).|  
|SCC_OP_SILENTOPEN|0x00000002L|No preguntar al usuario crear un proyecto. simplemente devuelva `SCC_E_UNKNOWNPROJECT`.|  
  
## <a name="get-flags"></a>Obtener marcas  
 Estas marcas se usan por el [SccGet](../extensibility/sccget-function.md) y [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Marcar|Value|DESCRIPCIÓN|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|El IDE está pasando los directorios, no archivos: Obtener todos los archivos en estos directorios.|  
|`SCC_GET_RECURSIVE`|0x00000002L|El IDE está pasando directorios: Obtenga estos directorios y todos sus subdirectorios.|  
  
## <a name="noption-values"></a>Valores de nOption  
 Estas marcas se usan por el [SccSetOption](../extensibility/sccsetoption-function.md) en el `nOption` parámetro.  
  
|Marcar|Valor|DESCRIPCIÓN|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Establecer estado de la cola de eventos.|  
|`SCC_OPT_USERDATA`|0x00000002L|Especificar los datos de usuario para `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|El IDE puede controlar la cancelación|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Establece una devolución de llamada para los cambios de nombre.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Deshabilitar la desprotección de interfaz de usuario del complemento de control de origen y no se establece el directorio de trabajo.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Agregar desde el sistema de control de código fuente para especificar un directorio de trabajo. Intente compartir en el proyecto asociado, si es un descendiente directo.|  
  
## <a name="dwval-bitflags"></a>dwVal marcadores de bits  
 Estas marcas se usan por el [SccSetOption](../extensibility/sccsetoption-function.md) en el `dwVal` parámetro.  
  
|Marcar|Valor|DESCRIPCIÓN|Utilizado por `nOption` valor|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Suspende la actividad de la cola de eventos.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Habilita el registro de cola de eventos.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|(Valor predeterminado) No tiene ningún modo Cancelar; complemento debe proporcionar si lo desea.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|IDE controla la cancelación.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|(Valor predeterminado) Aceptar desproteger desde la interfaz de usuario de complemento; se establece el directorio de trabajo.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|Ningún complemento retirada de la interfaz de usuario, ningún directorio de trabajo.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Vea también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
