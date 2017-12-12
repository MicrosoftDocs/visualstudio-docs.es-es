---
title: "Cómo usar Boost.Test para C++ en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0710a8-8e8a-4f6e-8415-5ab3eb830079
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6bfce4aa4153d8f01fa9ef6cd6dc0d4b08eedbc4
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Cómo usar Boost.Test para C++ en Visual Studio
En la **versión 15.5 de Visual Studio 2017** y en versiones posteriores, Boost.Test se integra en el IDE de Visual Studio como un componente de la carga de trabajo de **desarrollo para el escritorio con C++**. Para instalarlo en su equipo, abra al Instalador de Visual Studio y busque **Boost.Test Adapter** en la lista de componentes de carga de trabajo:

![Instalar Boost.Test](media/cpp-boost-component.png "Instalar Boost.Test para C++")

## <a name="install-boost"></a>Instalar Boost

 Boost.Test requiere [Boost](http://www.boost.org/)! Si no tiene Boost instalado, se recomienda que use el administrador de paquetes de Vcpkg. 

1. Siga las instrucciones de [Vcpkg: Administrador de paquetes de C++ para Windows](/cpp/vcpkg) para instalar vcpkg (si aún no lo tiene).
2. Ejecute `vcpkg install boost` para instalar las bibliotecas de Boost.
3. Ejecute el comando `vcpkg integrate install` para configurar Visual Studio con la biblioteca e incluir rutas de acceso a los archivos de encabezado y binarios de Boost. 

## <a name="create-a-project-for-your-tests"></a>Crear un proyecto para las pruebas
En la versión 15.5 de Visual Studio de 2017 no hay plantillas de proyecto o de elemento de prueba preconfiguradas para Boost.Test. Por lo tanto, tendrá que crear un proyecto de aplicación de consola que contenga las pruebas. Está previsto que en una versión futura de Visual Studio haya plantillas de prueba para Boost.Test. 

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo de la solución y elija **Agregar | Nuevo proyecto**. 
2. En el panel izquierdo, elija **Escritorio de Windows** y, después, elija **Aplicación de consola Windows** en el panel central. 
3. Asigne un nombre al proyecto y haga clic en **Aceptar**. 

## <a name="add-include-directives"></a>Agregar directivas include
En el archivo .cpp de prueba, agregue las directivas `#include` que sean necesarias para que los tipos y funciones del programa estén visibles en el código de prueba. El programa suele estar un nivel por encima en la jerarquía de carpetas. Si escribe `#include "../"`, se abrirá una ventana de IntelliSense donde podrá seleccionar la ruta de acceso completa al archivo de encabezado.

![Agregar directivas #include](media/cpp-gtest-includes.png "Agregar directivas #include al archivo .cpp de prueba")

Debe incluir como mínimo la [variante de encabezado único de Boost.Test](http://www.boost.org/doc/libs/1_48_0/libs/test/doc/html/utf/user-guide/usage-variants/single-header-variant.html) con `#include <path>/unit_test.hpp` y definir `BOOST_TEST_MODULE`. El siguiente ejemplo es suficiente para que la prueba se pueda detectar en el **Explorador de pruebas**:

```cpp
#include "stdafx.h"
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp>
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual();
    BOOST_CHECK(name == mc.GetName());
}
```

## <a name="write-and-run-tests"></a>Escribir y ejecutar pruebas
Ya está listo para escribir y ejecutar pruebas de Boost Test. Vea la [documentación de la biblioteca de Boost Test](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html) para más información sobre las macros de prueba. Vea [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md) para más información sobre cómo detectar, ejecutar y agrupar las pruebas usando el **Explorador de pruebas**.

## <a name="see-also"></a>Vea también
[Escribir pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)


  







