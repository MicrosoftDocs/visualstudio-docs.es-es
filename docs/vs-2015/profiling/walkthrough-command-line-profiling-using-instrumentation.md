---
title: 'Tutorial: Generación de perfiles de línea de comandos utilizando la instrumentación | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a37350cf274fbb551326ac96387330b0f3956e7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439697"
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>Tutorial: Línea de comandos de generación de perfiles mediante instrumentación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial le guiará a través de la generación de perfiles de una aplicación independiente de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] para recopilar información de tiempo detallada y llamar a datos del contador mediante el método de instrumentación de las herramientas de generación de perfiles. En este tutorial, se realizarán las siguientes tareas:  
  
- Utilizar la herramienta de línea de comandos [VSInstr](../profiling/vsinstr.md) para generar binarios instrumentados.  
  
- Utilizar la herramienta [VSPerfCLREnv](../profiling/vsperfclrenv.md) para establecer las variables de entorno para recopilar datos de generación de perfiles de .NET.  
  
- Utilizar la herramienta [VSPerfCmd](../profiling/vsperfcmd.md) para recopilar datos de generación de perfiles.  
  
- Utilizar la herramienta [VSPerfReport](../profiling/vsperfreport.md) para generar informes basados en archivos de los datos de generación de perfiles.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
- [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]  
  
- Conocimientos intermedios de C#  
  
- Conocimientos intermedios del uso de herramientas de la línea de comandos  
  
- Una copia de la [muestra PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md)  
  
- Para trabajar con la información proporcionada por la generación de perfiles, es preferible disponer de la información de símbolos de depuración. Para obtener más información, vea [Cómo: Información de símbolos de referencia Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>Generación de perfiles de la línea de comandos mediante el método de instrumentación  
 La instrumentación es un método de generación de perfiles mediante el cual versiones de los binarios de los que se generan perfiles creadas especialmente contienen funciones de sondeo que recopilan información de tiempo en la entrada y salida de funciones en un módulo instrumentado. Dado que este método de generación de perfiles es más invasor que el muestreo, conlleva una mayor cantidad de sobrecarga. Los binarios instrumentados también son más grandes que los binarios de depuración o lanzamiento, y no están pensados para su implementación.  
  
> [!NOTE]
> No envíe binarios instrumentados a los clientes. Los binarios instrumentados pueden contener varios riesgos. Los binarios incluyen información que facilita realizar ingeniería inversa de la aplicación, así como los riesgos de seguridad.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>Para generar perfiles de aplicación PeopleTrax mediante el método de instrumentación  
  
1. Instale la aplicación de ejemplo PeopleTrax y compile la versión de lanzamiento.  
  
2. Abra una ventana del símbolo del sistema y agregue el directorio de las **herramientas de generación de perfiles** a la variable de entorno local Path.  
  
3. Cambie el directorio de trabajo por el directorio que contiene los binarios de PeopleTrax.  
  
4. Cree un directorio para que contenga los informes basados en archivos. Escriba el comando siguiente:  
  
    ```  
    md Reports  
    ```  
  
5. Utilice la herramienta de línea de comandos VSInstr para instrumentar los binarios de la aplicación. Escriba los siguientes comandos en líneas de comandos separadas:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Nota** De forma predeterminada, VSInstr guarda una copia de seguridad no instrumentada del archivo original. El nombre de archivo de copia de seguridad tiene la extensión .orig. Por ejemplo, la versión original de "MyApp.exe" se guardaría como "MiAplic.exe.orig".  
  
6. Escriba el comando siguiente para establecer las variables de entorno adecuadas:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7. Escriba el siguiente comando para iniciar el generador de perfiles:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8. Después de iniciar el generador de perfiles en modo de seguimiento, ejecute la versión instrumentada del proceso PeopleTrax.exe para recopilar datos.  
  
     Aparecerá la ventana de la aplicación **PeopleTrax**.  
  
9. Haga clic en **Get People**.  
  
     La cuadrícula de datos de PeopleTrax se rellena con datos.  
  
10. Haga clic en **Exportar datos**.  
  
     Se iniciará el Bloc de notas con un nuevo archivo que contiene una lista de personas de la aplicación de **PeopleTrax**.  
  
11. Cierre el Bloc de notas y después cierre la aplicación **PeopleTrax**.  
  
12. Cierre el generador de perfiles. Escriba el comando siguiente:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Escriba el siguiente comando para restablecer las variables de entorno:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Use la herramienta VSPerfReport para generar o separar por comas archivos de informes de valores (.csv). Tipo:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Puede analizar los informes generados en un programa de hoja de cálculo, o bien puede usar el IDE de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para analizar los datos de generación de perfiles en el archivo Report.vsp. Para obtener más información, consulte [Analizar datos de las herramientas de rendimiento](../profiling/analyzing-performance-tools-data.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre las sesiones de rendimiento](../profiling/performance-session-overview.md)   
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)   
 [Vistas de informes de rendimiento](../profiling/performance-report-views.md)
