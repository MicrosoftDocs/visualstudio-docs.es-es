---
title: 'Tutorial: Uso de las API del generador de perfiles | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6c6d4a5fce3bbd3d050d3aaae4908b59d745596
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468215"
---
# <a name="walkthrough-using-profiler-apis"></a>Tutorial: Uso de las API del generador de perfiles

En el tutorial se usa una aplicación de C# para mostrar cómo usar las API de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Usará la API del generador de perfiles para limitar la cantidad de datos que se recopilan durante la generación de perfiles de instrumentación.  
  
 Normalmente, los pasos de este tutorial se aplican a una aplicación de C/C++. Para cada lenguaje, tendrá que configurar de forma adecuada el entorno de compilación.  
  
 Normalmente, empezará a analizar el rendimiento de la aplicación mediante la generación de perfiles de ejemplo. Si la generación de perfiles de ejemplo no proporciona información que localiza un cuello de botella, la generación de perfiles de instrumentación puede proporcionar un nivel de detalle mayor. La generación de perfiles de instrumentación es muy útil para investigar la interacción de los subprocesos.  
  
 Pero un nivel de detalle mayor significa que se recopilan más datos. Es posible que compruebe que la generación de perfiles de instrumentación crea archivos de datos grandes. Además, es más probable que la instrumentación afecte al rendimiento de la aplicación. Para más información, vea [Introducción a los valores de datos de instrumentación](../profiling/understanding-instrumentation-data-values.md) e [Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)  
  
 El generador de perfiles de Visual Studio le permite limitar la recopilación de datos. En este tutorial se ofrece un ejemplo de cómo limitar la recopilación de datos mediante las API del generador de perfiles. El generador de perfiles de Visual Studio proporciona una API para controlar la recopilación de datos desde dentro de una aplicación.  
  
 Para el código nativo, las API del generador de perfiles de Visual Studio se encuentran en *VSPerf.dll*. El archivo de encabezado (*VSPerf.h*) y la biblioteca de importación (*VSPerf.lib*) se encuentran en el directorio *Microsoft Visual Studio 9\Team Tools\Performance Tools*.  
  
 Para el código administrado, las API del generador de perfiles se encuentran en *Microsoft.VisualStudio.Profiler.dll*. Este archivo DLL se encuentra en el directorio *Microsoft Visual Studio 9\Team Tools\Performance Tools*. Para obtener más información, vea <xref:Microsoft.VisualStudio.Profiler>.  
  
## <a name="prerequisites"></a>Requisitos previos  
 En este tutorial se da por supuesto que la elección del entorno de desarrollo está configurada para admitir la depuración y el muestreo. En los temas siguientes se proporciona una introducción de estos requisitos previos:  
  
 [Elección de métodos de recopilación](../profiling/how-to-choose-collection-methods.md)  
  
 [Referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)  
  
 De forma predeterminada, cuando se inicia el generador de perfiles, recopila datos en el nivel global. El código siguiente al principio del programa desactiva la generación de perfiles global.  
  
```csharp  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Puede desactivar la recopilación de datos en la línea de comandos sin usar una llamada de API. En los pasos siguientes se supone que el entorno de compilación de línea de comandos está configurado para ejecutar las herramientas de generación de perfiles y las herramientas de desarrollo. Esto incluye la configuración necesaria para VSInstr y VSPerfCmd. Vea las [herramientas de generación de perfiles de línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md).  
  
## <a name="limit-data-collection-using-profiler-apis"></a>Limitación de la recopilación de datos mediante las API del generador de perfiles  
  
#### <a name="to-create-the-code-to-profile"></a>Para crear el código para generar perfiles  
  
1.  Cree un nuevo proyecto de C# en Visual Studio, o use una compilación de línea de comandos, según sus preferencias.  
  
    > [!NOTE]
    >  La compilación debe hacer referencia a la biblioteca *Microsoft.VisualStudio.Profiler.dll*, ubicada en el directorio *Microsoft Visual Studio 9\Team Tools\Performance Tools*.  
  
2.  Copie y pegue el código siguiente en el proyecto:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication1  
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

                    A a = new A(2);  
                    Console.WriteLine("2 square is {0}", a.DoNotProfileThis()); 

                    DataCollection.StartProfile(  
                    ProfileLevel.Global,  
                    DataCollection.CurrentId);

                    int x;  
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
  
#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Para recopilar y ver los datos en el IDE de Visual Studio  
  
1.  Abra el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En el menú **Analizar**, apunte a **Generador de perfiles** y después seleccione **Nueva sesión de rendimiento**.  
  
2.  Agregue el binario compilado a la lista **Destinos** en la ventana **Explorador de rendimiento**. Haga clic con el botón derecho en **Destinos** y después seleccione **Agregar binario de destino**. Localice el binario en el cuadro de diálogo **Agregar binario de destino** y después haga clic en **Abrir**.  
  
3.  En la barra de herramientas del **Explorador de rendimiento**, en la lista **Método**, haga clic en **Instrumentación**.  
  
4.  Haga clic en **Iniciar con generación de perfiles**.  
  
     El generador de perfiles instrumentará y ejecutará el archivo binario, y creará un archivo de informe de rendimiento. El archivo de informe de rendimiento aparecerá en el nodo **Informes** del **Explorador de rendimiento**.  
  
5.  Abra el archivo de informe de rendimiento resultante.  
  
 De forma predeterminada, cuando se inicia el generador de perfiles, recopilará los datos en el nivel global. El código siguiente al principio del programa desactiva la generación de perfiles global.  
  
```csharp  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### <a name="to-collect-and-view-data-at-the-command-line"></a>Para recopilar y ver los datos en la línea de comandos  
  
1.  Compile una versión de depuración del código de ejemplo que creó en el procedimiento "Crear el código para generar perfiles", anteriormente en este tutorial.  
  
2.  Para generar perfiles de una aplicación administrada, escriba el comando siguiente para establecer las variables de entorno adecuadas:  
  
     **VsPerfCLREnv /traceon**  
  
3.  Escriba el comando siguiente: **VSInstr \<nombreDeArchivo>.exe**  
  
4.  Escriba el comando siguiente: **VSPerfCmd /start:trace /output:\<nombreDeArchivo>.vsp**  
  
5.  Escriba el comando siguiente: **VSPerfCmd /globaloff**  
  
6.  Ejecute el programa.  
  
7.  Escriba el comando siguiente: **VSPerfCmd /shutdown**  
  
8.  Escriba el comando siguiente: **VSPerfReport /calltrace:\<nombreDeArchivo>.vsp**  
  
     Se crea un archivo .*csv* en el directorio actual con los datos de rendimiento resultantes.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Referencia de la API del generador de perfiles de Visual Studio (nativa)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Introducción](../profiling/getting-started-with-performance-tools.md)   
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)
