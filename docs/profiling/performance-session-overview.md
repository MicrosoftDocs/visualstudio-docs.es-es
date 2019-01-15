---
title: Información general sobre las sesiones de rendimiento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b673bad7bbcd552140cca25cc5a3fe90404c0716
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867178"
---
# <a name="performance-session-overview"></a>Información general sobre las sesiones de rendimiento
Esta introducción explica los conceptos básicos de la generación de perfiles. Los desarrolladores que no tienen experiencia en el trabajo de rendimiento verán cómo las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pueden ayudarles a ser productivos rápidamente y a aumentar el rendimiento de su código. Los desarrolladores con experiencia en la generación de perfiles pueden obtener una visión general de las características específicas y procesos de las herramientas.  
  
 Las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] le ayudarán a identificar problemas de rendimiento en el código fuente y a comparar el rendimiento de las soluciones posibles. La configuración predeterminada y los asistentes de las herramientas de generación de perfiles pueden proporcionarle información inmediata sobre muchos problemas de rendimiento. Las características y opciones de las herramientas de generación de perfiles proporcionan un control minucioso sobre el proceso de generación de perfiles. Este control incluye el destino preciso de las secciones de código, la recopilación de información de tiempo a nivel de bloque y la inclusión de datos adicionales de rendimiento de procesador y de sistema.  
  
 Los siguientes pasos constituyen el proceso básico de uso de las herramientas de generación de perfiles:  
  
1. Configure la sesión de rendimiento especificando el método de colección y los datos que se van a recopilar.  
  
2. Ejecute la aplicación en la sesión de rendimiento para recopilar datos de generación de perfiles.  
  
3. Analice los datos para identificar el problema de rendimiento.  
  
4. Modifique el código en el entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para aumentar el rendimiento de la aplicación del código  
  
5. Recopile datos de generación de perfiles del código modificado y compare los datos originales y modificados.  
  
6. Genere un informe que documente el aumento del rendimiento.  
  
   Para trabajar con la información proporcionada por la generación de perfiles, debe tener información de símbolos disponible para los archivos binarios de los cuales desea generar perfiles y para los archivos binarios del sistema operativo Windows.  
  
## <a name="configure-the-performance-session"></a>Configurar la sesión de rendimiento  
 Para configurar una sesión de generación de perfiles, seleccione el método de generación de perfiles que desea utilizar y los datos que se van a recopilar. El **Asistente de rendimiento** de las herramientas de generación de perfiles puede guiarle a través de la configuración básica y puede utilizar las páginas de propiedades de la sesión de rendimiento para agregar más opciones:  
  
- Los métodos de generación de perfiles incluyen el muestreo, el seguimiento y la asignación de memoria.  
  
- Los valores de datos incluyen el tiempo, los contadores de rendimiento del sistema operativo y del procesador, y los eventos de aplicación como los errores de página y las transiciones del kernel.  
  
  Puede configurar una sesión de rendimiento en un proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como parte de la solución del proyecto o generar perfiles de binarios arbitrarios a través del IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Puede especificar las propiedades de la sesión en las páginas de propiedades de la sesión de rendimiento o puede usar al Asistente para la generación de perfiles.  
  
## <a name="collect-profiling-data"></a>Recopilar datos de generación de perfiles  
 Inicie la recopilación de datos de generación de perfiles desde el **Explorador de rendimiento**. Puede pausar y reanudar la generación de perfiles para limitar la cantidad de datos que se recopilan. También puede asociar un proceso que ya se está ejecutando.  
  
 En cuanto se inicia la aplicación, la ventana **Control de recopilación de datos** aparece en el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Desde la ventana **Control de recopilación de datos**, puede generar perfiles de partes específicas de la aplicación pausando y reanudando el proceso de recopilación. También puede utilizar la ventana **Control de recopilación de datos** para insertar marcas en los datos que se recopilan. Las marcas son puntos de datos definidos por el usuario que se muestran en las vistas de perfil y que se pueden utilizar para filtrar los datos de generación de perfiles.  
  
 Cuando se cierra la aplicación de destino, las herramientas de generación de perfiles generan un archivo de datos de generación de perfiles (*.vsp) y muestran la vista Informe de resumen en el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="analyze-the-data-and-identify-performance-issues"></a>Analizar los datos e identificar problemas de rendimiento  
 Cuando finaliza un proceso de generación de perfiles, los datos se analizan y se muestra un resumen en la ventana de la vista **Informe de rendimiento** de las herramientas de generación de perfiles. Se recopilan datos de generación de perfiles para la pila de llamadas y las funciones individuales de la aplicación de destino. Las vistas de informe muestran el análisis de rendimiento para los rangos de datos de los procesos, subprocesos, módulos, funciones y líneas de código fuente de la aplicación. Los valores de los datos de generación de perfiles para una función incluyen los siguientes:  
  
- El tiempo total empleado en la función y en las funciones secundarias a las que llamó la función (valores inclusivos).  
  
- El tiempo dedicado a ejecutar solo el código de la función (valores exclusivos).  
  
  Más de doce vistas distintas permiten analizar los datos de generación de perfiles de la manera más eficaz. Las personalizaciones de vistas permiten filtrar y ordenar los datos para encontrar las funciones que podrían estar causando problemas de rendimiento. El filtrado de ruta de acceso activa permite resaltar de forma inmediata las rutas de acceso más activas en las vistas Árbol de llamadas y Módulo.  
  
## <a name="modify-the-application-code"></a>Modificar el código de la aplicación  
 Una vez haya aislado uno o más problemas de rendimiento pertinentes, puede modificar el código mediante el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y después recopilar datos de generación de perfiles para los cambios.  
  
## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Volver a recopilar datos de generación de perfiles y comparar los datos entre los procesos de generación de perfiles  
 La vista Informe de comparación de herramientas de generación de perfiles muestra las diferencias en el módulo, la función o el rendimiento de línea entre dos archivos de datos de generación de perfiles seleccionados. Puede especificar los valores de datos de generación de perfiles que desea comparar y alternar entre la vista Comparación y las vistas de los archivos individuales.  
  
## <a name="generate-a-report-of-the-results"></a>Generar un informe de los resultados  
 Puede pegar filas de cualquier vista de informe de rendimiento en mensajes de correo electrónico y hojas de cálculo, y puede generar informes que contengan los datos para una o más vistas.  
  
## <a name="see-also"></a>Vea también  
 [Temas de introducción](../profiling/overviews-performance-tools.md)   
 [Tutorial: Identificación de problemas de rendimiento](/visualstudio/profiling/beginners-guide-to-cpu-sampling)