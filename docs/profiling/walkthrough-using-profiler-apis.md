---
title: "Tutorial: Uso de las API del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de rendimiento, tutoriales"
  - "herramientas de generación de perfiles, tutoriales"
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Tutorial: Uso de las API del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El tutorial utiliza una aplicación de C\# para mostrar cómo se utilizan las API de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Se usarán las API del generador de perfiles para limitar la cantidad de datos que se recopilan durante la generación de perfiles de instrumentación.  
  
 Los pasos de este tutorial se aplican por lo general a una aplicación de C\/C\+\+.  Para cada lenguaje, tendrá que configurar adecuadamente el entorno de compilación.  
  
 Normalmente, comenzará a analizar el rendimiento de la aplicación utilizando la generación de perfiles de muestreo.  Si la generación de perfiles de muestreo no proporciona información que señale con precisión un cuello de botella, la generación de perfiles de instrumentación puede proporcionar un nivel de detalle mayor.  La generación de perfiles de instrumentación es muy útil para investigar la interacción de subprocesos.  
  
 Sin embargo, un nivel mayor de detalle implica que se recogen más datos.  Observará que la generación de perfiles de instrumentación crea grandes archivos de datos.  Asimismo, es más probable que la instrumentación afecte al rendimiento de la aplicación.  Para obtener más información, vea [Introducción a los valores de datos de instrumentación](../profiling/understanding-instrumentation-data-values.md) y [Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md).  
  
 El generador de perfiles de Visual Studio le permite limitar la recolección de datos.  Este tutorial proporciona un ejemplo de cómo limitar la recolección de datos mediante la utilización de las API del generador de perfiles.  El generador de perfiles de Visual Studio proporciona una API para controlar la recolección de datos desde el interior de una aplicación.  
  
 Las API del generador de perfiles de Visual Studio están en VSPerf.dll. para el código nativo.  El archivo de encabezado, VSPerf.h, y la biblioteca de importación, VSPerf.lib, se encuentran en el directorio Microsoft Visual Studio 9\\Team Tools\\Performance Tools.  
  
 Para el código administrado, las API del generador de perfiles están en Microsoft.VisualStudio.Profiler.dll.  Esta DLL se encuentra en el directorio Microsoft Visual Studio 9\\Team Tools\\Performance Tools.  Para obtener más información, vea <xref:Microsoft.VisualStudio.Profiler>.  
  
## Requisitos previos  
 En este tutorial se da por supuesto que ha configurado la opción del entorno de desarrollo para que admita la depuración y el muestreo.  Los temas siguientes proporcionan una información general de estos requisitos previos:  
  
 [Cómo: Elegir métodos de recolección](../profiling/how-to-choose-collection-methods.md)  
  
 [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)  
  
 De forma predeterminada, cuando se inicia el generador de perfiles, éste recopila datos globales.  El código siguiente colocado al principio del programa desactiva la generación de perfiles global.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Puede desactivar la recolección de datos en la línea de comandos sin utilizar llamadas API.  En los pasos siguientes se da por supuesto que su entorno de compilación de línea de comandos se ha configurado para ejecutar las herramientas de generación de perfiles, así como las herramientas de desarrollo.  Esto incluye los valores necesarios para VSInstr y VSPerfCmd.  Vea Herramientas de generación de perfiles de la línea de comandos.  
  
## Limitar la recopilación de datos mediante las API del generador de perfiles  
  
#### Para crear código de generación de perfiles  
  
1.  Cree un nuevo proyecto C\# en Visual Studio o utilice una compilación de línea de comandos, según lo que prefiera.  
  
    > [!NOTE]
    >  Su compilación debe hacer referencia a la biblioteca Microsoft.VisualStudio.Profiler.dll, ubicada en el directorio Microsoft Visual Studio 9\\Team Tools\\Performance Tools.  
  
2.  Copie y pegue el código siguiente en su proyecto:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
    {  
        class Program  
        {  
            public class A  
            {  
             private int _x;  
  
             public A(int x)  
             {  
              _x = x;  
             }  
  
             public int DoNotProfileThis()  
             {  
              return _x * _x;  
             }  
  
             public int OnlyProfileThis()  
             {  
              return _x + _x;  
             }  
  
             public static void Main()  
             {  
            DataCollection.StopProfile(  
            ProfileLevel.Global,  
            DataCollection.CurrentId);  
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
              x = a.OnlyProfileThis();  
              DataCollection.StopProfile(  
                  ProfileLevel.Global,   
                  DataCollection.CurrentId);  
              Console.WriteLine("2 doubled is {0}", x);  
             }  
            }  
  
        }  
    }  
    ```  
  
#### Para recopilar y ver datos en el IDE de Visual Studio  
  
1.  Abra el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  En el menú **Analizar**, seleccione **Generador de perfiles** y, a continuación, elija **Nueva sesión de rendimiento**.  
  
2.  Agregue el binario compilado a la lista **Destinos** en la ventana **Explorador de rendimiento**.  Haga clic con el botón secundario en **Destinos** y, a continuación, seleccione **Agregar binario de destino**.  Busque el binario en el cuadro de diálogo **Agregar binario de destino** y, a continuación, haga clic en **Abrir**.  
  
3.  Seleccione **Instrumentación** en la lista **Método** de la barra de herramientas del **Explorador de rendimiento**.  
  
4.  Haga clic en **Iniciar con generación de perfiles**.  
  
     El generador de perfiles instrumentará y ejecutará el binario y creará un archivo de informe de rendimiento.  Este archivo aparecerá en el nodo **Informes** del **Explorador de rendimiento**.  
  
5.  Abra el archivo de informe de rendimiento resultante.  
  
 De forma predeterminada, cuando se inicia el generador de perfiles, éste recopilará datos globales.  El código siguiente colocado al principio del programa desactiva la generación de perfiles global.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### Para recopilar y ver los datos en la línea de comandos  
  
1.  Compile una versión de depuración del código de ejemplo que creó en el procedimiento "Para crear código de generación de perfiles", más arriba en este tutorial.  
  
2.  Para generar los perfiles de una aplicación administrada, escriba el comando siguiente para establecer las variables de entorno correspondientes:  
  
     VsPefCLREnv \/traceon  
  
3.  Escriba el comando siguiente: VSInstr \<filename.exe\>  
  
4.  Escriba el comando siguiente: VSPerfCmd \/start:trace \/output:\<filename.vsp\>  
  
5.  Escriba el comando siguiente:VSPerfCmd \/globaloff  
  
6.  Ejecute el programa.  
  
7.  Escriba el comando siguiente:VSPerfCmd \/shutdown  
  
8.  Escriba el comando siguiente: VSPerfReport \/calltrace:\<filename.vsp\>  
  
     Se creará un archivo .csv en el directorio actual con los datos de rendimiento resultantes.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Referencia a la API del generador de perfiles de Visual Studio \(Nativa\)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Introducción](../profiling/getting-started-with-performance-tools.md)   
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)