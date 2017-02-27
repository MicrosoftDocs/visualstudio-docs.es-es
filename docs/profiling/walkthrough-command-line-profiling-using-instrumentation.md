---
title: "Tutorial: Generar perfiles utilizando la instrumentaci&#243;n en la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, tutoriales"
  - "herramientas de rendimiento, tutoriales"
  - "herramientas de rendimiento, herramientas de línea de comandos"
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Tutorial: Generar perfiles utilizando la instrumentaci&#243;n en la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial explica el procedimiento para generar el perfil de una aplicación de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] independiente para recopilar datos detallados sobre el control de tiempo y el recuento de llamadas usando el método de instrumentación de las herramientas de generación de perfiles.  En este tutorial, llevará a cabo las tareas siguientes:  
  
-   Usar la herramienta de línea de comandos [VSInstr](../profiling/vsinstr.md) para generar binarios instrumentados.  
  
-   Usar la herramienta [VSPerfCLREnv](../profiling/vsperfclrenv.md) para establecer las variables de entorno para recopilar los datos de generación de perfiles de .NET Framework.  
  
-   Usar la herramienta [VSPerfCmd](../profiling/vsperfcmd.md) para recopilar los datos de generación de perfiles.  
  
-   Usar la herramienta [VSPerfReport](../profiling/vsperfreport.md) para generar informes basados en archivos con los datos de generación de perfiles.  
  
## Requisitos previos  
  
-   [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]  
  
-   Conocimientos intermedios de C\#  
  
-   Conocimientos intermedios del uso de herramientas de la línea de comandos  
  
-   Una copia de [Ejemplo de PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md).  
  
-   Para trabajar con la información proporcionada por la generación de perfiles, es preferible disponer de la información de símbolos de depuración.  Para obtener más información, vea [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
## Generación de perfiles mediante el método de instrumentación en la línea de comandos  
 La instrumentación es un método de generación de perfiles en el que se compilan especialmente versiones los binarios cuyos perfiles se compilan. Estas versiones contienen funciones de análisis que recopilan información de control de tiempos en los puntos de entrada y salida de las funciones del módulo instrumentado.  Dado que este método de generación de perfiles es más invasor que el muestreo, provoca una sobrecarga mayor.  Los binarios instrumentados también son más grandes que los binarios de depuración o lanzamiento, y no están pensados para su implementación.  
  
> [!NOTE]
>  No envíe archivos binarios instrumentados a los clientes.  Los archivos binarios instrumentados pueden encerrar varios riesgos.  Los binarios incluyen información que permite realizar fácilmente ingeniería inversa en la aplicación y entrañan riesgos para la seguridad.  
  
#### Para generar perfiles de la aplicación PeopleTrax utilizando el método de instrumentación  
  
1.  Instale la aplicación de ejemplo PeopleTrax y compile la versión de lanzamiento.  
  
2.  Abra una ventana del símbolo del sistema y agregue el directorio **Herramientas de generación de perfiles** a la variable de entorno local Path.  
  
3.  Cambie el directorio de trabajo por el directorio que contiene los binarios de PeopleTrax.  
  
4.  Cree un directorio para contener los informes basados en archivos.  Escriba el comando siguiente:  
  
    ```  
    md Reports  
    ```  
  
5.  Use la herramienta de línea de comandos VSInstr para instrumentar los binarios en la aplicación.  Escriba los siguientes comandos en líneas de comandos independientes:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Nota:** de forma predeterminada, VSInstr guarda una copia de seguridad no instrumentada del archivo original.  El nombre del archivo de copia de seguridad tiene la extensión .orig.  Por ejemplo, la versión original de "MyApp.exe" se guardaría como "MyApp.exe.orig".  
  
6.  Escriba el comando siguiente para establecer las variables de entorno adecuadas:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7.  Escriba el siguiente comando para iniciar el generador de perfiles:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8.  Después de iniciar el generador de perfiles en modo de seguimiento, ejecute la versión instrumentada del proceso PeopleTrax.exe para recopilar los datos.  
  
     Aparecerá la ventana de la aplicación **PeopleTrax**.  
  
9. Haga clic en **Get People**.  
  
     La cuadrícula de datos de PeopleTrax se rellena con datos.  
  
10. Haga clic en **Exportar datos**.  
  
     Se iniciará el Bloc de notas con un nuevo archivo que contiene una lista de personas de la aplicación **PeopleTrax**.  
  
11. Cierre el Bloc de notas y, a continuación, cierre la aplicación **PeopleTrax**.  
  
12. Apague el generador de perfiles.  Escriba el comando siguiente:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Escriba el siguiente comando para restablecer las variables de entorno:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Use la herramienta VSPerfReport para generar archivos de informe de valores separados por comas \(.csv\).  Escriba:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Puede analizar los informes generados en un programa de hoja de cálculo o puede usar el entorno de desarrollo integrado \(IDE\) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para analizar los datos de generación de perfiles en el archivo Report.vsp.  Para obtener más información, vea [Analizar los datos de las Herramientas de generación de perfiles](../profiling/analyzing-performance-tools-data.md).  
  
## Vea también  
 [Información general sobre las sesiones de rendimiento](../profiling/performance-session-overview.md)   
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)   
 [Vistas de informes de las herramientas de generación de perfiles](../profiling/performance-report-views.md)