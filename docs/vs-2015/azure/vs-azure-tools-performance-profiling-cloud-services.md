---
title: Probar el rendimiento de un servicio en la nube | Microsoft Docs
description: Probar el rendimiento de un servicio de nube mediante el generador de perfiles de Visual Studio
author: mikejo5000
manager: douge
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.tgt_pltfrm: multiple
ms.workload: na
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 25b60e5e4072a0523d17082a5c5646e5bb1ade6a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002406"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Prueba del rendimiento de un servicio en la nube
## <a name="overview"></a>Información general
Puede probar el rendimiento de un servicio en la nube de las maneras siguientes:

* Use diagnósticos de Azure para recopilar información sobre las solicitudes y conexiones y revisar las estadísticas del sitio que muestran cómo el servicio se realiza desde la perspectiva del cliente. Para empezar a usar, vea [configuración de diagnósticos para Azure Cloud Services y Virtual Machines](http://go.microsoft.com/fwlink/p/?LinkId=623009).
* Use el generador de perfiles de Visual Studio para obtener un análisis exhaustivo de los aspectos de cálculo de cómo se ejecuta el servicio. Como se describe en este tema, puede usar el generador de perfiles para medir el rendimiento como un servicio se ejecuta en Azure. Para obtener información acerca de cómo usar el generador de perfiles para medir el rendimiento como un servicio se ejecuta localmente en un emulador de proceso, consulte [probar el rendimiento de un servicio de nube de Azure localmente en el emulador de proceso con el Profiler de Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=262845).

## <a name="choosing-a-performance-testing-method"></a>Elegir un método de prueba de rendimiento
### <a name="use-azure-diagnostics-to-collect"></a>Use diagnósticos de Azure para recopilar:
* Estadísticas de las páginas web o servicios, como las solicitudes y conexiones.
* Estadísticas sobre roles, por ejemplo, ¿con qué frecuencia se reinicia un rol.
* En general conjunto de información sobre el uso de memoria, como el porcentaje de tiempo que tarda el recolector de elementos o la memoria de un rol en ejecución.

### <a name="use-the-visual-studio-profiler-to"></a>Use el generador de perfiles de Visual Studio para:
* Determine qué funciones requieren más tiempo.
* Mida el tiempo que tarda cada parte de un programa de cálculo intensivo.
* Comparar informes de rendimiento detallados para las dos versiones de un servicio.
* Analizar la asignación de memoria con más detalle que el nivel de las asignaciones de memoria individuales.
* Analizar los problemas de simultaneidad en el código multiproceso.

Cuando se utiliza el generador de perfiles, puede recopilar datos cuando se ejecuta un servicio en la nube localmente o en Azure.

### <a name="collect-profiling-data-locally-to"></a>Recopilar datos de perfiles localmente para:
* Probar el rendimiento de una parte de un servicio en la nube, como la ejecución del rol de trabajo específico, que no requiere una carga simulada realista.
* Probar el rendimiento de un servicio en la nube en aislamiento, en condiciones controladas.
* Probar el rendimiento de un servicio en la nube antes de implementarla en Azure.
* Probar el rendimiento de un servicio de nube privada, sin interrumpir las implementaciones existentes.
* Probar el rendimiento del servicio sin incurrir en gastos para que se ejecuta en Azure.

### <a name="collect-profiling-data-in-azure-to"></a>Recopilar datos de generación de perfiles en Azure para:
* Probar el rendimiento de un servicio en la nube bajo una carga simulada o real.
* Utilice el método de instrumentación de recopilar datos de generación de perfiles, como se describe más adelante en este tema.
* Probar el rendimiento del servicio en el mismo entorno que cuando se ejecuta el servicio en producción.

Normalmente, simula una carga para servicios en la nube de prueba en normal o condiciones de sobrecarga.

## <a name="profiling-a-cloud-service-in-azure"></a>Generación de perfiles de un servicio en la nube de Azure
Al publicar su servicio en la nube desde Visual Studio, puede generar perfiles del servicio y especificar la configuración de generación de perfiles que le proporcionarán la información que desee. Se inicia una sesión de generación de perfiles para cada instancia de un rol. Para obtener más información acerca de cómo publicar un servicio desde Visual Studio, consulte [publicación en un servicio de nube de Azure desde Visual Studio](https://msdn.microsoft.com/library/azure/ee460772.aspx).

Para conocer más acerca de los perfiles de rendimiento en Visual Studio, vea [guía básica para la generación de perfiles de rendimiento](https://msdn.microsoft.com/library/azure/ms182372.aspx) y [analizar el rendimiento de aplicaciones mediante las herramientas de generación de perfiles](https://msdn.microsoft.com/library/azure/z9z62c29.aspx).

> [!NOTE]
> Puede habilitar IntelliTrace o la generación de perfiles al publicar su servicio en la nube. No se puede habilitar ambas cosas.
> 
> 

### <a name="profiler-collection-methods"></a>Métodos de recopilación de Profiler
Puede usar los métodos de recopilación diferentes para la generación de perfiles, en función de los problemas de rendimiento:

* **Muestreo de la CPU** : este método recopila estadísticas de la aplicación que son útiles para el análisis inicial de los problemas de utilización de CPU. Muestreo de la CPU es el método sugerido para iniciar la mayoría de las investigaciones de rendimiento. Hay poca repercusión en la aplicación que está generando perfiles para recopilar datos de muestreo de CPU.
* **Instrumentación** : este método recopila datos detallados que son útiles para un análisis enfocado y para analizar problemas de rendimiento de entrada/salida. El método de instrumentación graba cada entrada, salida y llamada de función de las funciones en un módulo durante una generación de perfiles. Este método es útil para recopilar información de tiempo detallada sobre una sección del código y para entender el impacto de las operaciones de entrada y salida en el rendimiento de la aplicación. Este método está deshabilitado para un equipo que ejecuta un sistema operativo de 32 bits. Esta opción está disponible solo cuando se ejecuta el servicio en la nube en Azure, no localmente en el emulador de proceso.
* **Asignación de memoria .NET** : este método recopila datos de asignación de memoria de .NET Framework mediante el método de generación de perfiles de muestreo. Los datos recopilados incluyen el número y tamaño de los objetos asignados.
* **Simultaneidad** : este método recopila datos de contención de recursos y datos de ejecución de procesos y subprocesos que resultan útiles para analizar aplicaciones multiproceso y de varios procesos. El método de simultaneidad recopila datos de cada evento que bloquea la ejecución del código, como sucede cuando un subproceso espera que se libere el acceso bloqueado a un recurso de aplicación. Este método es útil para analizar aplicaciones multiproceso.
* También puede habilitar **la generación de perfiles de interacción de capas**, que proporciona información adicional sobre los tiempos de ejecución de ADO.NET sincrónicas llama a funciones de aplicaciones de varios niveles que se comunican con una o varias bases de datos. Puede recopilar datos de interacción de capas con cualquiera de los métodos de generación de perfiles. Para obtener más información sobre la generación de perfiles de interacción de capas, vea [vista interacciones de capas](https://msdn.microsoft.com/library/azure/dd557764.aspx).

## <a name="configuring-profiling-settings"></a>Configuración de las opciones de generación de perfiles
La siguiente ilustración muestra cómo establecer la configuración de generación de perfiles desde el cuadro de diálogo Publicar aplicación de Azure.

![Configurar valores de generación de perfiles](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> Para habilitar el **Habilitar generación de perfiles** casilla de verificación, debe tener instalado en el equipo local que está usando para publicar su servicio en la nube el generador de perfiles. De forma predeterminada, el generador de perfiles se instala al instalar Visual Studio.
> 
> 

### <a name="to-configure-profiling-settings"></a>Para configurar las opciones de generación de perfiles
1. En el Explorador de soluciones, abra el menú contextual del proyecto de Azure y, a continuación, elija **publicar**. Para obtener instrucciones detalladas sobre cómo publicar un servicio en la nube, consulte [publicar un servicio de nube mediante las herramientas de Azure](http://go.microsoft.com/fwlink/p?LinkId=623012).
2. En el **publicar aplicación de Azure** cuadro de diálogo, elija el **configuración avanzada** ficha.
3. Para habilitar la generación de perfiles, seleccione el **Habilitar generación de perfiles** casilla de verificación.
4. Para configurar las opciones de generación de perfiles, elija el **configuración** hyperlink. Aparece el cuadro de diálogo de configuración de generación de perfiles.
5. Desde el **¿qué método de generación de perfiles le gustaría usar** botones de opción, elija el tipo de generación de perfiles que necesita.
6. Para recopilar lo datos de generación de perfiles de interacción de capas, seleccione la **Habilitar generación de perfiles de interacción de capas** casilla de verificación.
7. Para guardar la configuración, elija la **Aceptar** botón.
   
    Al publicar esta aplicación, esta configuración se usa para crear la sesión de generación de perfiles para cada rol.

## <a name="viewing-profiling-reports"></a>Ver informes de generación de perfiles
Se crea una sesión de generación de perfiles para cada instancia de un rol de servicio en la nube. Para ver los informes de generación de perfiles de cada sesión en Visual Studio, puede ver la ventana del explorador de servidores y, a continuación, elija el nodo de proceso de Azure para seleccionar una instancia de un rol. A continuación, puede ver el informe de generación de perfiles como se muestra en la siguiente ilustración.

![Ver informe de generación de perfiles de Azure](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Para ver los informes de generación de perfiles
1. Para ver la ventana del explorador de servidores en Visual Studio, en la barra de menús elija Ver, Explorador de servidores.
2. Elija el nodo de proceso de Azure y, a continuación, elija el nodo de implementación de Azure para el servicio de nube que seleccionó para generar perfiles cuando publicó desde Visual Studio.
3. Para ver informes de generación de perfiles para una instancia, elija el rol en el servicio, abra el menú contextual para una instancia específica y, a continuación, elija **Ver informe de generación de perfiles**.
   
    El informe, un archivo .vsp, ahora se descarga desde Azure y el estado de la descarga aparece en el registro de actividad de Azure. Cuando se complete la descarga, el informe de generación de perfiles aparece en una pestaña en el editor de Visual Studio denominada <Role name> *<Instance Number>* <identifier>VSP. Datos de resumen para el informe aparecen.
4. Para mostrar diferentes vistas del informe, en la lista Vista actual, elija el tipo de vista que desee. Para obtener más información, consulte [vistas de informe de las herramientas de generación de perfiles](https://msdn.microsoft.com/library/azure/bb385755.aspx).

## <a name="next-steps"></a>Pasos siguientes
[Depuración de Cloud Services](https://msdn.microsoft.com/library/azure/ee405479.aspx)

[Publicación en un servicio de nube de Azure desde Visual Studio](https://msdn.microsoft.com/library/azure/ee460772.aspx)

