---
title: 'Tutorial: Generar perfiles utilizando el método de muestreo en la línea de comandos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6a0b43916a9a37937de0665a591555de3e2f7ad
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Tutorial: Generar perfiles mediante muestreo desde la línea de comandos

En este tutorial se muestra cómo generar perfiles para una aplicación utilizando las herramientas de la línea de comandos y el muestreo para identificar problemas de rendimiento.

En este tutorial, recorreremos paso a paso el proceso de generación de perfiles de una aplicación mediante herramientas de la línea de comandos, así como la utilización del muestreo para aislar e identificar los problemas de rendimiento de la aplicación.

En este tutorial realizará los siguientes pasos:

- Generar perfiles para una aplicación mediante herramientas de la línea de comandos y muestreo.
- Analizar los resultados de generación de perfiles mediante muestreo para buscar y corregir problemas de rendimiento.

## <a name="prerequisites"></a>Requisitos previos

- Conocimientos intermedios de [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]
- Conocimientos intermedios del uso de herramientas de la línea de comandos
- Una copia de la [muestra PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md)
- Para trabajar con la información proporcionada por la generación de perfiles, es preferible disponer de la información de símbolos de depuración.

## <a name="command-line-profiling-using-the-sampling-method"></a>Generación de perfiles mediante el método de muestreo en la línea de comandos

El muestreo es un método de generación de perfiles mediante el cual un proceso específico se sondea periódicamente para determinar la función activa. Los datos resultantes proporcionan un recuento de la frecuencia con que esa función ha estado en la parte superior de la pila de llamadas al muestrear el proceso.

> [!NOTE]
> Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \Team Tools\Performance Tools del directorio de instalación de Visual Studio. En equipos de 64 bits, están disponibles versiones de 64 bits y de 32 bits de las herramientas. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso a la variable de entorno PATH de la ventana de símbolo del sistema o agregarla al propio comando. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). PeopleTrax es una aplicación de 32 bits.

### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Para generar perfiles de la aplicación PeopleTrax utilizando el método de muestreo

1. Instale la aplicación de ejemplo PeopleTrax y compile la versión de lanzamiento de la aplicación.

2. Abra una ventana del símbolo del sistema y agregue el directorio Herramientas de generación de perfiles a la variable de entorno local Path.

3. Cambie el directorio de trabajo por el directorio que contiene los binarios de PeopleTrax.

4. Escriba el comando siguiente para establecer las variables de entorno adecuadas:

    ```cmd
    VSPerfCLREnv /sampleon
    ```

5. Inicie la generación de perfiles ejecutando VSPerfCmd.exe, que es la herramienta de la línea de comandos que controla el generador de perfiles. El comando siguiente inicia la aplicación y el generador de perfiles en modo de muestreo:

    ```cmd
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe
    ```

     El proceso del generador de perfiles se inicia y se asocia al proceso de PeopleTrax.exe. El proceso del generador de perfiles empieza a escribir los datos de perfiles recopilados en el archivo de informe.

6. Haga clic en **Get People**.

7. Haga clic en **ExportData**.

     Se abrirá el Bloc de notas con un nuevo archivo que contiene los datos exportados de **PeopleTrax**.

8. Cierre el Bloc de notas y después cierre la aplicación **PeopleTrax**.

9. Cierre el generador de perfiles. Escriba el comando siguiente:

    ```cmd
    VSPerfCmd /shutdown
    ```

10. Use el comando siguiente para restablecer las variables de entorno:

    ```cmd
    VSPerfCLREnv /sampleoff
    ```

11. Los datos de generación de perfiles se almacenan en el archivo .vsp. Analice los resultados usando uno de los métodos siguientes:

    - Abra el archivo .vsp en el IDE de Visual Studio.

         o

    - Genere un archivo de informes de valores separados por comas (.csv) utilizando la herramienta de línea de comandos VSPerfReport.exe. Para generar informes para usar fuera del IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], use el comando siguiente:

        ```cmd
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all
        ```

## <a name="see-also"></a>Vea también

[Información general sobre las sesiones de rendimiento](../profiling/performance-session-overview.md)  
[Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)  
[VSPerfCmd](../profiling/vsperfcmd.md)  
[Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)  
[Vistas de informes de rendimiento](../profiling/performance-report-views.md)