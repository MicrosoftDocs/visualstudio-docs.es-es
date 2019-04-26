---
title: Generar perfiles en clústeres HPC (Sistemas de alto rendimiento) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d93071aa62c4d2305b0104ec17e8242bacefa6d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62994995"
---
# <a name="profile-on-hpc-high-performance-computing-clusters"></a>Generar perfiles en clústeres HPC (informática de alto rendimiento)

Puede generar perfiles en nodos de ejecución de clústeres de Microsoft Windows HPC usando el método de muestreo de las Herramientas de generación de perfiles de Visual Studio. Para obtener más información sobre HPC, consulte [Windows HPC](https://azure.microsoft.com/solutions/big-compute/) en el sitio web de Microsoft.

## <a name="prerequisites"></a>Requisitos previos

Para generar perfiles en un nodo de ejecución HPC, debe hacer lo siguiente:

- Instale Microsoft HPC Pack 2008 en el mismo equipo en que está Visual Studio. El equipo no tiene que formar parte del clúster HPC. Puede instalar HPC Pack en el [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/?LinkID=177414).

- Instale el [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] y la versión independiente de las herramientas de generación de perfiles en el nodo de ejecución HPC. Los programas de instalación para el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] y el generador de perfiles independiente están disponibles en los medios de instalación de Visual Studio. **Nota** Debe reiniciar el proceso después de haber instalado [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] y antes de instalar las herramientas de generación de perfiles.

  Para instalar el [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] y las herramientas de generación de perfiles independientes en un nodo de ejecución de HPC activo y habilitar la generación de perfiles en el equipo del clúster, siga estos pasos:

1. Abra la ventana de símbolo del sistema que se instala con el paquete de HPC.

2. Escriba los siguientes comandos en símbolos del sistema separados:

    1. `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`

    2. `clusrun /all /scheduler:` *%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`

    3. `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`

| | |
|------------------| - |
| *%HeadNode%* | Nombre del nodo principal del clúster. |
| *%FxPath%* | Ruta de acceso al instalador de [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)]. En el medio de instalación de Visual Studio, la ruta de acceso es: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe |
| *%ProfilerPath%* | Ruta de acceso a la versión independiente del instalador de las herramientas de generación de perfiles. En el medio de instalación de Visual Studio, la ruta de acceso es: Standalone Profiler\x64\vs_profiler.exe |

## <a name="profile-on-an-hpc-compute-node"></a>Generación de perfiles en un nodo de ejecución HPC

Configure una sesión de generación de perfiles mediante el Asistente de rendimiento HPC para especificar la información de destino y de clúster de HPC. Puede establecer opciones adicionales en las páginas de propiedades de la sesión de rendimiento. Las herramientas de generación de perfiles implementan los binarios de destino necesarios e inician el generador de perfiles y la aplicación HPC automáticamente.

1. En el menú **Analizar**, haga clic en **Iniciar Asistente de rendimiento HPC**. Si el comando no está disponible, asegúrese de que tiene los requisitos previos mencionados anteriormente.

2. Haga clic en **Siguiente** en la primera página del asistente.

3. En la segunda página del asistente, seleccione la aplicación de la que desea generar perfiles.

   - Para generar perfiles de un proyecto que está abierto actualmente en [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], seleccione la opción **Uno o más proyectos disponibles** y después el nombre del proyecto de la lista.

   - Para generar perfiles de un binario que no está en un proyecto abierto, seleccione la opción **Un archivo ejecutable (un archivo .EXE)**.

4. Haga clic en **Siguiente**.

5. En la tercera página del asistente:

    - Si está generando perfiles de un archivo ejecutable que no está en un proyecto abierto, especifique la ruta de acceso al archivo binario en **¿Cuál es la ruta de acceso completa al archivo ejecutable?**

    - Si está generando perfiles de un archivo ejecutable que no está en un proyecto abierto, puede especificar argumentos de línea de comandos para pasar al proceso en **Argumentos de línea de comandos**.

    - En **Directorio de trabajo remoto**, especifique la ruta de acceso a la carpeta que se usa en las instancias de proceso en los nodos de ejecución individuales.

    - En **Ubicación de implementación**, especifique la ruta de acceso al directorio que el servidor HPC usa para organizar las imágenes para la implementación.

6. Haga clic en **Siguiente**.

7. En la cuarta página del asistente:

    - En lista **Nodo principal**, haga clic en el equipo que actúa como el nodo principal de HPC en la generación de perfiles. El nodo principal puede ser "localhost", lo que permite generar perfiles en el equipo local sin necesidad de un clúster.

    - En la lista **Número de procesos**, haga clic en el número de instancias de la aplicación que se ejecutarán.

    - Desde la lista **Opciones de generación de perfiles**, seleccione el destino de generación de perfiles.

         Para generar perfiles de un proceso concreto en el clúster, seleccione la opción **Perfil en el rango** y después el rango del proceso en la lista desplegable.

         Para generar perfiles del proceso o procesos que se ejecutan en un nodo concreto del clúster HPC, seleccione la opción **Perfil en el nodo** y después el nodo de la lista desplegable.

8. Haga clic en **Siguiente**.

9. En la quinta página del asistente, puede elegir iniciar inmediatamente el generador de perfiles y el proceso de generación de perfiles o iniciar la generación de perfiles más tarde mediante el Explorador de rendimiento.

    - Seleccione **Iniciar la generación de perfiles cuando finalice el asistente** para empezar a generar perfiles inmediatamente o desactive la casilla para empezar a generar perfiles manualmente.

10. Haga clic en **Finalizar**.

## <a name="set-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Establecer las propiedades de generación de perfiles de HPC usando las páginas de propiedades de la sesión de rendimiento

Puede cambiar las propiedades de la sesión de rendimiento que estableció en el Asistente para generación de perfiles de HPC en la página Propiedades de inicio de HPC de la página de propiedades de la sesión de rendimiento. Establezca las opciones adicionales en la página Propiedades avanzadas de HPC.

### <a name="to-open-the-performance-session-property-pages"></a>Para abrir las páginas de propiedades de la sesión de rendimiento

1. Si es necesario, abra el archivo de sesión de rendimiento (.psess) en el Explorador de rendimiento. En el menú **Archivo**, haga clic en **Abrir** y busque el archivo.

2. En el Explorador de rendimiento, haga clic con el botón derecho en el nombre de la sesión y después haga clic en **Propiedades**.

3. En el cuadro de diálogo Páginas de propiedades, use uno de los siguientes métodos:

    - Haga clic en **General** y después seleccione **Recopilar en clúster HPC** para activar la generación de perfiles de HPC o desmarque la casilla para desactivarla.

    - Haga clic en **Propiedades de inicio de HPC** para cambiar las propiedades que inician la aplicación HPC.

    - Haga clic en **Propiedades avanzadas de HPC** para establecer opciones adicionales

### <a name="hpc-launch-properties"></a>Propiedades de inicio de HPC

|Propiedad.|Descripción|
|--------------|-----------------|
|**Nodo principal**|Especifica el equipo que actúa como el nodo principal de HPC en la generación de perfiles.|
|**Número de procesos**|Especifica el número de instancias de la aplicación que se ejecutan en la aplicación perfilada.|
|**Perfil en el rango**|Para generar perfiles de un proceso concreto en el clúster, seleccione la opción **Perfil en el rango** y después el rango del proceso en la lista desplegable.|
|**Perfil en el nodo**|Para generar perfiles del proceso o procesos que se ejecutan en un nodo concreto del clúster HPC, seleccione la opción **Perfil en el nodo** y después el nodo de la lista desplegable.|
|**Directorio de trabajo remoto**|Especifica la ruta de acceso a la carpeta que se usa en las instancias de proceso en los nodos de ejecución individuales.|
|**Ubicación de implementación**|Especifica la ruta de acceso al directorio que el servidor HPC usa para organizar las imágenes para la implementación.|

### <a name="advanced-properties"></a>Propiedades avanzadas

| Propiedad. | Descripción |
|---------------------------------------| - |
| **Nombre del proyecto** | Muestra el nombre del proyecto o la solución de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] actual. |
| **Limpiar cuando se detenga el generador de perfiles** | Cuando es true, quita los binarios que se han implementado en el directorio de ejecución. Los archivos y directorios creados por el programa de usuario no se quitan en este paso. Si el directorio de ejecución y el de implementación fueron creados por el IDE, el IDE intentará quitarlos, pero no podrá hacerlo si tienen archivos no implementados por el IDE. |
| **Archivos adicionales para implementar** | Especifica una lista separada por puntos y comas de los archivos adicionales para implementar en el nodo de ejecución. Puede hacer clic en el botón de puntos suspensivos (**...**) para seleccionar varios archivos mediante un cuadro de diálogo. |
| **Comando Mpiexec** | Especifica la aplicación que inicia la aplicación de MPI. El valor predeterminado es **mpiexec.exe** |
| **Argumentos Mpiexec** | Especifica los argumentos para pasar al comando de mpiexec.exe. |
| **Nodos solicitados en el clúster** | Especifica el número de nodos en el clúster en los que se va a ejecutar la aplicación. |
| **Implementar archivos CRT** | Cuando es true, implementa el runtime de C/C++ en el clúster. |
| **Script anterior a la generación de perfiles** | Especifica la ruta de acceso y el nombre de archivo de un script que se ejecutará en el equipo de desarrollo local antes de iniciar la sesión de generación de perfiles. |
| **Argumentos de script anteriores a la generación de perfiles** | Especifica los argumentos para pasar al script que se ejecuta antes de la generación de perfiles. |
| **Script posterior a la generación de perfiles** | Especifica la ruta de acceso y el nombre de archivo de un script que se ejecutará en el equipo de desarrollo local después de finalizar la sesión de generación de perfiles. |
| **Argumentos de script posteriores a la generación de perfiles** | Especifica los argumentos para pasar al script que se ejecuta después de la generación de perfiles. |
