---
title: Pruebas unitarias de aplicaciones C++ existentes con el Explorador de pruebas | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: 040e3f0a236067a96d107f64f4c9aca06d0706e3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566443"
---
# <a name="unit-testing-existing-c-applications-with-test-explorer"></a>Pruebas unitarias de aplicaciones C++ existentes con el Explorador de pruebas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [pruebas unitarias de aplicaciones C++ existentes con el Explorador de pruebas](https://docs.microsoft.com/visualstudio/test/unit-testing-existing-cpp-applications-with-test-explorer).  
  
Se recomienda que, antes de cambiar una aplicación existente, se asegure de que tiene buena cobertura con pruebas unitarias. Así podrá confiar en que los cambios no han introducido errores. Si la aplicación todavía no tiene pruebas unitarias, se pueden agregar mediante las técnicas que se muestran en este tema. En este tema se describe cómo agregar pruebas unitarias para código Visual C++ existente, comenzando por decidir cómo probar el código y cómo crear, escribir y, por último, ejecutar las pruebas.  
  
## <a name="deciding-how-to-test-your-code"></a>La decisión sobre cómo probar el código  
 Abra el proyecto existente de C++ e inspecciónelo para decidir cómo desea agregar las pruebas unitarias. Quizá desee utilizar herramientas de modelado, que ayudan a ver las dependencias del código y ayudan a entender cómo interactúan las partes. Para más información, vea [Visualizar el código](../modeling/visualize-code.md).  
  
 Se recomienda separar los cambios en pequeñas tareas. Antes de cada pequeño cambio, escriba pruebas unitarias para los aspectos del comportamiento que permanezcan invariables. Estas pruebas seguirán completándose correctamente después de realizar el cambio. Por ejemplo, si planea cambiar una función de ordenación de modo que ordene una lista de personas por apellido en lugar de por nombre, puede escribir una prueba unitaria que compruebe que todos los nombres de entrada aparecen en la salida. Después de realizar el cambio, se pueden agregar nuevas pruebas unitarias para el nuevo comportamiento.  
  
 Si resulta práctico, muchas de las pruebas unitarias o todas ellas deben utilizar solo las funciones que se exportan. No obstante, si se cambia solo una pequeña parte de toda la aplicación, quizá desee utilizar funciones que no se exporten. Por ejemplo, quizás desee que las pruebas invoquen funciones internas o pruebas que establezcan y obtengan los valores de variables internas.  
  
 Hay varias maneras de probar el código del producto, según si expone las interfaces que desea probar. Elija una de las siguientes formas:  
  
 **Las pruebas unitarias usarán solo las funciones que se exportan del código en pruebas:**  
 Agregue un proyecto de prueba independiente. En el proyecto de prueba, agregue una referencia al proyecto en pruebas.  
  
 Vaya al procedimiento [Para hacer referencia a funciones exportadas del proyecto de prueba](#projectRef).  
  
 **El código en pruebas se compila como un archivo .exe:**  
 Agregue un proyecto de prueba independiente. Vincúlelo al archivo objeto de salida.  
  
 Vaya al procedimiento [Para vincular las pruebas a los archivos de biblioteca u objeto](#objectRef).  
  
 **Las pruebas unitarias deben usar funciones y datos privados y el código en pruebas puede compilarse como una biblioteca estática:**  
 Cambie el proyecto en pruebas para compilarlo como un archivo .lib. Agregue un proyecto de prueba independiente que haga referencia al proyecto en pruebas.  
  
 Este enfoque tiene la ventaja de permitir que las pruebas utilicen miembros privados, pero sigue manteniendo las pruebas en un proyecto independiente. Sin embargo, puede no ser adecuado para algunas aplicaciones donde se debe tener una biblioteca de vínculos dinámicos (.dll).  
  
 Vaya al procedimiento [Para cambiar el código en pruebas a una biblioteca estática](#staticLink).  
  
 **Las pruebas unitarias deben usar funciones y datos privados, y el código debe compilarse como una biblioteca de vínculos dinámicos (DLL):**  
 Agregue las pruebas unitarias en el mismo proyecto que el código de producto.  
  
 Vaya al procedimiento [Para agregar pruebas unitarias en el mismo proyecto](#sameProject).  
  
## <a name="creating-the-tests"></a>Crear las pruebas  
  
###  <a name="staticLink"></a> Para cambiar el código en pruebas a una biblioteca estática  
  
-   Si las pruebas deben utilizar miembros que no exporte un proyecto en pruebas y el proyecto en pruebas se compila como una biblioteca dinámica, considere convertirla en una biblioteca estática.  
  
    1.  En el Explorador de soluciones, en el menú contextual del proyecto en pruebas, seleccione **Propiedades**. Se abrirá la ventana de propiedades del proyecto.  
  
    2.  Seleccione **Propiedades de configuración**, **General**.  
  
    3.  Establezca **Tipo de configuración** en **Biblioteca estática (.lib)**.  
  
 Continúe con el procedimiento [Para vincular las pruebas a los archivos de biblioteca u objeto](#objectRef).  
  
###  <a name="projectRef"></a> Para hacer referencia a funciones exportadas del proyecto de prueba  
  
-   Si un proyecto en pruebas exporta funciones que desea probar, puede agregar una referencia al proyecto de código desde el proyecto de prueba.  
  
    1.  Cree un proyecto de prueba C++.  
  
        1.  En el menú **Archivo**, seleccione **Nuevo**, **Proyecto**, **Visual C++, Prueba**, **Proyecto de prueba unitaria C++**.  
  
    2.  En el Explorador de soluciones, en el menú contextual del proyecto de prueba, seleccione **Referencias**. Se abrirá la ventana de propiedades del proyecto.  
  
    3.  Seleccione **Propiedades comunes**, **Marco de trabajo y referencias** y después haga clic en el botón **Agregar nueva referencia**.  
  
    4.  Seleccione **Proyectos** y, después, el proyecto que se va a probar.  
  
         Elija el botón de **Agregar** .  
  
    5.  En las propiedades del proyecto de prueba, agregue la ubicación del proyecto en pruebas a los directorios de archivos de inclusión.  
  
         Seleccione **Propiedades de configuración**, **Directorios de VC++**, **Directorios de archivos de inclusión**.  
  
         Elija **Editar** y agregue el directorio del encabezado del proyecto en pruebas.  
  
 Vaya a [Escritura de las pruebas unitarias](#addTests).  
  
###  <a name="objectRef"></a> Para vincular las pruebas a los archivos de biblioteca u objeto  
  
-   Si el código en pruebas no exporta las funciones que quiere probar, puede agregar el archivo de salida **.obj** o **.lib** a las dependencias del proyecto de prueba.  
  
    1.  Cree un proyecto de prueba C++.  
  
        1.  En el menú **Archivo**, seleccione **Nuevo**, **Proyecto**, **Visual C++, Prueba**, **Proyecto de prueba unitaria C++**.  
  
    2.  En el Explorador de soluciones, en el menú contextual del proyecto de prueba, seleccione **Propiedades**. Se abrirá la ventana de propiedades del proyecto.  
  
    3.  Elija **Propiedades de configuración**, **Enlazador**, **Entrada**, **Dependencias adicionales**.  
  
         Seleccione **Editar** y agregue los nombres de los archivos **.obj** o **.lib**. No utilice nombres de ruta de acceso completa.  
  
    4.  Elija **Propiedades de configuración**, **Enlazador**, **General**, **Directorios de bibliotecas adicionales**.  
  
         Seleccione **Editar** y agregue la ruta del directorio de los archivos **.obj** o **.lib**. La ruta de acceso está normalmente dentro de la carpeta de compilación del proyecto en pruebas.  
  
    5.  Seleccione **Propiedades de configuración**, **Directorios de VC++**, **Directorios de archivos de inclusión**.  
  
         Elija **Editar** y agregue el directorio del encabezado del proyecto en pruebas.  
  
 Vaya a [Escritura de las pruebas unitarias](#addTests).  
  
###  <a name="sameProject"></a> Para agregar pruebas unitarias en el mismo proyecto  
  
1.  Modifique las propiedades del proyecto de código del producto para incluir los encabezados y los archivos de biblioteca que se requieren para pruebas unitarias.  
  
    1.  En el Explorador de soluciones, en el acceso directo del proyecto en pruebas, elija Propiedades. Se abrirá la ventana de propiedades del proyecto.  
  
    2.  Seleccione **Propiedades de configuración**, **Directorios de VC++**.  
  
    3.  Edite los directorios de inclusión y de biblioteca:  
  
        |||  
        |-|-|  
        |**Directorios de archivos de inclusión**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|  
        |**Directorios de archivos de bibliotecas**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|  
  
2.  Agregue el archivo de prueba unitaria de C++:  
  
    -   En el Explorador de soluciones, en el acceso directo del proyecto, seleccione **Agregar**, **Nuevo elemento** y **Pruebas unitarias de C++**.  
  
 Vaya a [Escritura de las pruebas unitarias](#addTests).  
  
##  <a name="addTests"></a> Escritura de las pruebas unitarias  
  
1.  En cada archivo de código de prueba unitaria, agregue un fragmento `#include` para los encabezados de proyecto en pruebas.  
  
2.  Agregue las clases y los métodos de prueba a los archivos de código de prueba unitaria. Por ejemplo:  
  
    ```cpp  
    #include "stdafx.h"  
    #include "CppUnitTest.h"  
    #include "MyProjectUnderTest.h"  
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
    namespace MyTest  
    {  
      TEST_CLASS(MyTests)  
      {  
      public:  
          TEST_METHOD(MyTestMethod)  
          {  
              Assert::AreEqual(MyProject::Multiply(2,3), 6);  
          }  
      };  
    }  
    ```  
  
 Para más información, vea [Pruebas unitarias de código nativo con el Explorador de pruebas](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c).  
  
## <a name="run-the-tests"></a>Ejecutar las pruebas  
  
1.  En el menú **Ver** , elija **Otras ventanas**, **Explorador de pruebas**.  
  
2.  En el Explorador de pruebas, elija **Ejecutar todas**.  
  
 Para más información, vea [Inicio rápido: Desarrollo basado en pruebas con el Explorador de pruebas](../test/quick-start-test-driven-development-with-test-explorer.md).



