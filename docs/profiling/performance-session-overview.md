---
title: "Informaci&#243;n general sobre las sesiones de rendimiento de las herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Herramientas de generación de perfiles, sesiones de rendimiento"
  - "sesiones de rendimiento"
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
caps.latest.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 35
---
# Informaci&#243;n general sobre las sesiones de rendimiento de las herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta sección de información general se explican los aspectos básicos de la generación de perfiles.  Los desarrolladores que no tienen experiencia en el trabajo de rendimiento verán cómo las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede ayudarles a alcanzar rápidamente la productividad necesaria y a aumentar el rendimiento del código que generan.  Los desarrolladores con experiencia en la generación de perfiles pueden obtener información general sobre características y procesos concretos de las herramientas de generación de perfiles.  
  
 Las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayudan a identificar los problemas de rendimiento del código fuente y a comparar el rendimiento de las posibles soluciones.  Los asistentes de las herramientas de generación de perfiles y la configuración predeterminada proporcionan una perspectiva que permite identificar inmediatamente numerosos problemas de rendimiento.  Las características y las opciones de las herramientas de generación de perfiles proporcionan un control minucioso del proceso de generación de perfiles.  Este control incluye el destino preciso de las secciones de código, la recolección de información de control de tiempo de nivel de bloque y la inclusión de datos adicionales del procesador y de rendimiento del sistema en sus datos.  
  
 Los pasos siguientes constituyen el proceso básico para el uso de las herramientas de generación de perfiles:  
  
1.  Configurar la sesión de rendimiento; para ello, especifique el método de recolección y los datos que desea recopilar.  
  
2.  Recopilar los datos de generación de perfiles mediante la ejecución de la aplicación en la sesión de rendimiento.  
  
3.  Analizar los datos para identificar el problema de rendimiento.  
  
4.  Modificar el código en el entorno de desarrollo integrado \(IDE\) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para aumentar el rendimiento de aplicación del código  
  
5.  Recopilar los datos de generación de perfiles del código modificado y compararlos con los originales.  
  
6.  Generar un informe que documente el aumento del rendimiento.  
  
 Para trabajar con la información proporcionada por la generación de perfiles, debe tener información de símbolos para los binarios de los que desea generar perfiles y para los del sistema operativo Windows.  
  
## Configurar la sesión de rendimiento  
 Para configurar una sesión de generación de perfiles, seleccione el método de generación de perfiles que desea utilizar y los datos que va a recopilar.  El **Asistente de rendimiento** de las herramientas de generación de perfiles sirve como guía para la configuración básica; además, puede utilizar las páginas de propiedades de la sesión de rendimiento para agregar más opciones.  
  
-   Entre los métodos de generación de perfiles se incluyen el muestreo, la traza y la asignación de memoria.  
  
-   Entre los valores de datos se incluyen los contadores de rendimiento del sistema operativo, procesador y tiempo, y eventos de aplicación como errores de página y transiciones del kernel.  
  
 Puede configurar una sesión de rendimiento en un proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como parte de la solución de proyectos o generar perfiles de binarios arbitrarios a través del IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Para especificar las propiedades de la sesión, utilice las páginas de propiedades de la sesión de rendimiento o bien el asistente para la generación de perfiles.  
  
## Recopilar datos de generación de perfiles  
 Inicie la recopilación de datos de generación de perfiles desde el **Explorador de rendimiento**.  Puede pausar y reanudar la generación de perfiles para limitar la cantidad de datos que se recopila.  También puede establecer una asociación a un proceso que ya se está ejecutando.  
  
 En cuanto se inicia la aplicación, aparece la ventana **Control de recolección de datos** en el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Desde la ventana **Control de recolección de datos** puede generar perfiles de partes concretas de la aplicación mediante la pausa y la reanudación del proceso de recolección.  También puede utilizar la ventana **Control de recolección de datos** para insertar marcas en los datos que se recopilan.  Las marcas son puntos de datos definidos por el usuario que aparecen en las vistas de perfil y que pueden utilizarse para filtrar los datos de generación de perfiles.  
  
 Cuando se cierra la aplicación de destino, las herramientas de generación de perfiles crean un archivo de datos de generación de perfiles \(\*.vsp\) y muestran la vista de informe de resumen en el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Analizar los datos e identificar los problemas de rendimiento  
 Al terminar de ejecutar una generación de perfiles, se analizan los datos y se muestra un resumen en las ventanas de la vista **Informe de rendimiento** de las herramientas de generación de perfiles.  Los datos de la generación de perfiles se recopilan para la pila de llamadas y funciones individuales de la aplicación de destino.  Las vistas de informe muestran el análisis del rendimiento de rangos de datos de los procesos, subprocesos, módulos, funciones y líneas de código fuente de la aplicación.  Entre los valores de datos de generación de perfiles de una función se incluyen los siguientes:  
  
-   El tiempo total invertido en la función y en las funciones secundarias llamadas por la función \(valores inclusivos\).  
  
-   El tiempo invertido en ejecutar solamente el código de la función \(valores exclusivos\).  
  
 Hay más de doce vistas diferentes que permiten analizar los datos de generación de perfiles de la forma más eficaz.  Las personalizaciones de las vistas permiten filtrar y ordenar los datos para buscar las funciones que puedan estar causando problemas de rendimiento.  El filtrado de la ruta de acceso activa resalta de inmediato las rutas de acceso más activas en las vistas Árbol de llamadas y Módulo.  
  
## Modificar el código de la aplicación  
 Después de haber aislado los problemas de rendimiento pertinentes, puede modificar el código mediante el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y, a continuación, recopilar datos de generación de perfiles para realizar cambios.  
  
## Recopilar de nuevo los datos de generación de perfiles y comparar los datos de las distintas generaciones  
 La vista de informe de comparación de las herramientas de generación de perfiles muestra la diferencia de rendimiento del módulo, la función o la línea entre dos archivos de datos de generación de perfiles seleccionados.  Puede especificar los valores de datos de generación de perfiles que desea comparar y cambiar entre la vista de comparación y las vistas de los archivos individuales.  
  
## Generar un informe de los resultados  
 Puede pegar filas de cualquier vista de informe de rendimiento en correo electrónicos y hojas de cálculo y generar informes que contengan datos de una o más vistas.  
  
## Vea también  
 [Temas de introducción](../profiling/overviews-performance-tools.md)   
 [Tutorial: Generar perfiles de aplicaciones](../profiling/walkthrough-identifying-performance-problems.md)