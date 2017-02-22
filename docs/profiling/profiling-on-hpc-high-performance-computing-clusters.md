---
title: "Generar perfiles en cl&#250;steres HPC (Sistemas de alto rendimiento) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.hpc.wizard.exeoptions"
  - "vs.performance.hpc.wizard.summary"
  - "vs.performance.hpc.wizard.startoptions"
  - "vs.performance.hpc.wizard.intro"
  - "vs.performance.hpc.property.basic"
  - "vs.performance.hpc.wizard.application"
  - "vs.performance.hpc.wizard.clusteroptions"
  - "vs.performance.hpc.property.advanced"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, HPC"
  - "generación de perfiles de HPC"
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Generar perfiles en cl&#250;steres HPC (Sistemas de alto rendimiento)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede perfilar los nodos de cálculo de los clústeres de Microsoft Windows HPC usando el método de muestreo de las herramientas de generación de perfiles [!INCLUDE[vsPreExt](../profiling/includes/vspreext_md.md)] o [!INCLUDE[vsUltExt](../profiling/includes/vsultext_md.md)].  Para obtener más información sobre HPC vea [HPC de Windows](http://go.microsoft.com/fwlink/?LinkId=165393) en el sitio web de Microsoft.  
  
## Requisitos previos  
 Para perfilar un nodo de cálculo de HPC, debe hacer el siguiente:  
  
-   Instalar Microsoft HPC Pack 2008 en el mismo equipo que [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  El equipo no tiene que formar parte del clúster HPC.  Puede instalar HPC en [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/?LinkID=177414).  
  
-   Instalar [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] y la versión independiente de las herramientas de generación de perfiles en el nodo de cálculo de HPC.  Instale los programas tanto para el perfilador [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] como para el perfilador independiente. Ambos están disponibles en el disco de instalación de [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)].  **Nota** Debe reiniciar el equipo después de haber instalado [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] y antes de instalar las herramientas de generación de perfiles.  
  
 Para instalar [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] y las herramientas de generación de perfiles independientes en un nodo de cálculo de HPC activo y habilitar la generación de perfiles en la máquina del clúster, siga estos pasos:  
  
1.  Abra la ventana del símbolo del sistema que se instala con el paquete de HPC.  
  
2.  Escriba los siguientes comandos en símbolos del sistema diferentes:  
  
    1.  `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`  
  
    2.  `clusrun /all /scheduler:` *%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3.  `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`  
  
|||  
|-|-|  
|*%HeadNode%*|Nombre del nodo principal del clúster.|  
|*%FxPath%*|Ruta de acceso al instalador de [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)].  En el disco de instalación de [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)], la ruta de acceso es: WCU\\dotNetFramework\\dotNetFx40\_Full\_x86\_x64.exe|  
|*%ProfilerPath%*|Ruta de acceso a la versión independiente del instalador de las herramientas de generación de perfiles.  En el disco de instalación [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)], la ruta de acceso es: Standalone Profiler\\x64\\vs\_profiler.exe|  
  
## Perfilar un nodo de cálculo de HPC  
 Para configurar una sesión de generación de perfiles, use el Asistente de rendimiento HPC para especificar la información de destino y el clúster HPC.  Puede establecer otras opciones adicionales en las páginas de propiedades de la sesión de rendimiento.  Las herramientas de generación de perfiles implementan automáticamente los archivos binarios de destino necesarios e inician el generador de perfiles y la aplicación HPC.  
  
#### Para perfilar un nodo de cálculo de HPC  
  
1.  En el menú **Analizar**, haga clic en **Iniciar Asistente de rendimiento HPC**.  Si el comando no está disponible, asegúrese de que cumple los requisitos previos mencionados anteriormente.  
  
2.  En la primera página del asistente, haga clic en **Siguiente**.  
  
3.  En la segunda página del asistente, seleccione la aplicación que desea perfilar.  
  
    -   Para perfilar un proyecto que está actualmente abierto en [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], seleccione la opción **Uno o varios proyectos disponibles** y, a continuación, seleccione el nombre del proyecto en la lista.  
  
    -   Para perfilar un archivo binario que no está en un proyecto abierto, seleccione la opción **Un archivo ejecutable \(archivo .EXE\)**.  
  
4.  Haga clic en **Siguiente**.  
  
5.  En la tercera página del asistente:  
  
    -   Si está perfilando un archivo ejecutable que no se encuentra en un proyecto abierto, especifique la ruta de acceso al archivo binario en **¿Cuál es la ruta de acceso al archivo ejecutable?**.  
  
    -   Si está perfilando un archivo ejecutable que no se encuentra en un proyecto abierto, puede especificar argumentos de la línea de comandos para pasar al proceso en **Argumentos de la línea de comandos**.  
  
    -   En **Directorio de trabajo remoto**, especifique la ruta de acceso a la carpeta que usan las instancias del proceso en cada uno de los nodos de cálculo.  
  
    -   En **Ubicación de implementación**, especifique la ruta de acceso al directorio que el servidor del HPC usa para organizar las imágenes para la implementación.  
  
6.  Haga clic en **Siguiente**.  
  
7.  En la cuarta página del asistente:  
  
    -   En la lista **Nodo principal**, haga clic en el equipo que actúa como nodo principal de HPC en la generación de perfiles.  El nodo principal puede ser "localhost", que le permite perfilar el equipo local sin la necesidad de un clúster.  
  
    -   En la lista **Número de procesos**, haga clic en el número de instancias de la aplicación que se van a ejecutar.  
  
    -   En la lista **Opciones de generación de perfiles**, seleccione el destino de la generación de perfiles.  
  
         Para perfilar un proceso concreto en el clúster, seleccione la opción **Perfil en el rango** y, a continuación, seleccione el rango del proceso en la lista desplegable.  
  
         Para perfilar el proceso o procesos que se ejecutan en un nodo concreto del clúster HPC, seleccione la opción **Perfil en el nodo** y, a continuación, seleccione el nodo en la lista desplegable.  
  
8.  Haga clic en **Siguiente**.  
  
9. En la quinta página del asistente, puede optar por iniciar inmediatamente el generador de perfiles y el proceso de generación de perfiles o por iniciar la generación de perfiles posteriormente a través del Explorador de rendimiento.  
  
    -   Seleccione **Iniciar generación de perfiles cuando finalice el asistente** para empezar a perfilar inmediatamente o desactive la casilla para empezar a perfilar manualmente.  
  
10. Haga clic en **Finalizar**.  
  
## Establecer las propiedades de generación de perfiles de HPC usando las páginas de propiedades de la sesión de rendimiento  
 Puede cambiar las propiedades de la sesión de rendimiento que estableció en el Asistente para generación de perfiles de HPC en la página Propiedades de inicio HPC de la sesión de rendimiento.  Puede establecer otras opciones adicionales en la página Propiedades avanzadas de HPC.  
  
#### Para abrir las páginas de propiedades de la sesión de rendimiento  
  
1.  Si es necesario, abra el archivo de sesión de rendimiento \(.psess\) en el Explorador de rendimiento.  En el menú **Archivo**, haga clic en **Abrir** y busque el archivo.  
  
2.  En el Explorador de rendimiento, haga clic con el botón secundario en el nombre de la sesión de rendimiento y, a continuación, haga clic en **Propiedades**.  
  
3.  En el cuadro de diálogo Páginas de propiedades, use uno de los métodos siguientes:  
  
    -   Haga clic en **General** y, a continuación, active la casilla **Recopilar en clúster HPC** para habilitar la generación de perfiles de HPC o desactívela para deshabilitar la generación de perfiles de HPC.  
  
    -   Haga clic en **Propiedades de inicio HPC** para cambiar las propiedades que inician la aplicación HPC.  
  
    -   Haga clic en **Propiedades avanzadas de HPC** para establecer más opciones  
  
### Propiedades de inicio HPC  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|**Nodo principal**|Especifica el equipo que actúa como nodo principal durante la generación de perfiles.|  
|**Número de procesos**|Especifica el número de instancias de la aplicación que se van a ejecutar en la aplicación perfilada.|  
|**Perfil en el rango**|Para perfilar un proceso concreto en el clúster, seleccione la opción **Perfil en el rango** y, a continuación, seleccione el rango del proceso en la lista desplegable.|  
|**Perfilar en el nodo**|Para perfilar el proceso o procesos que se ejecutan en un nodo concreto del clúster HPC, seleccione la opción **Perfil en el nodo** y, a continuación, seleccione el nodo en la lista desplegable.|  
|**Directorio de trabajo remoto**|Especifica la ruta de acceso a la carpeta que usan las instancias del proceso en cada uno de los nodos de cálculo.|  
|**Ubicación de la implementación**|Especifica la ruta de acceso al directorio que el servidor HPC usa para organizar las imágenes para la implementación.|  
  
### Avanzadas \(Propiedades\)  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|**Nombre del proyecto**|Nombre del proyecto o solución actual de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].|  
|**Limpiar cuando se detenga el generador de perfiles**|Cuando es TRUE, quita los archivos binarios que se han implementado en el directorio de ejecución.  Los archivos y directorios creados por el programa del usuario no se quitan en este paso.  Si el IDE creó el directorio de ejecución y el directorio de implementación, el IDE intentará quitarlos, pero no podrá hacerlo si tienen archivos que el IDE no ha implementado.|  
|**Archivos adicionales para implementar**|Especifica una lista de los archivos adicionales que se van a implementar en el nodo de cálculo separados por punto y coma.  Puede hacer clic en el botón de puntos suspensivos \(**...**\) para seleccionar varios archivos utilizando un cuadro de diálogo.|  
|**Comando mpiexec**|Especifica la aplicación que inicia la aplicación MPI.  El valor predeterminado es **mpiexec.exe**.|  
|**Argumentos mpiexec**|Especifica los argumentos que se van a pasar al comando mpiexec.exe.|  
|**Nodos solicitados del clúster**|Especifica el número de nodos del clúster en los que se ejecuta la aplicación.|  
|**Implementar archivos CRT**|Cuando es TRUE, implementa el tiempo de ejecución de C\/C\+\+ en el clúster.|  
|**Script anterior a la generación de perfiles**|Especifica la ruta de acceso y el nombre de archivo de un script que se va a ejecutar en el equipo de desarrollo local antes de que la sesión de generación de perfiles se inicie.|  
|**Argumentos de script anterior a la generación de perfiles**|Especifica los argumentos que se van a pasar al script anterior a la generación de perfiles.|  
|**Script posterior a la generación de perfiles**|Especifica la ruta de acceso y el nombre de archivo de un script que se va a ejecutar en el equipo de desarrollo local una vez que la sesión de generación de perfiles finalice.|  
|**Argumentos de script posterior a la generación de perfiles**|Especifica los argumentos que se van a pasar al script posterior a la generación de perfiles.|