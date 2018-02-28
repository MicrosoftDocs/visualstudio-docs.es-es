---
title: "Introducción a las pruebas unitarias: crear planes de pruebas | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit testing, create unit test plans
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e6789c3a8ddb9b0aa317df0d2362d39946069cbd
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="get-started-with-unit-testing"></a>Introducción a las pruebas unitarias

Use Visual Studio para definir y ejecutar sus pruebas unitarias para conservar el estado del código, garantizar la cobertura del código y para detectar errores antes de que los clientes lo hagan.

<a name="create-tests"></a>
## <a name="create-unit-tests"></a>Crear pruebas unitarias

Cree pruebas unitarias y ejecútelas con frecuencia para asegurarse de que el código funciona correctamente.

1. Cree un proyecto de prueba unitaria.
        
   ![Agregar un proyecto de prueba unitaria a la solución](media/createunittest1.png)
    
1. Dé un nombre al proyecto.
        
   ![Plantilla de proyecto de prueba unitaria](media/createunittest2.png)
  
   El proyecto se agrega a la solución.
    
   ![Proyecto de prueba unitaria en el Explorador de soluciones](media/createunittest5.png)
    
1. En el proyecto de prueba unitaria, agregue una referencia al proyecto que quiere probar.
        
   ![Agregar una referencia al proyecto de prueba unitaria](media/createunittest6.png)
    
1. Seleccione el proyecto que contiene el código que va a probar.
        
   ![Seleccionar la referencia que se va a agregar](media/createunittest7.png)
    
1. Codifique la prueba unitaria.

   ![Agregar código a la prueba unitaria](media/createunittest8.png) 

También puede crear códigos auxiliares de método de pruebas unitarias con el [comando **Crear pruebas unitarias**](create-unit-tests-menu.md).
O puede usar un [marco de prueba unitaria diferente](#frameworks) para crear pruebas para los diferentes lenguajes de código.

![Usar el comando Crear pruebas unitarias](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Ejecutar pruebas unitarias

1. Abra el Explorador de pruebas.
        
   ![En el menú Prueba, abra el Explorador de pruebas.](media/rununittest1.png) 

1. Ejecute las pruebas unitarias.
        
   ![Ejecutar pruebas unitarias en el Explorador de pruebas](media/rununittest2.png) 

   Puede ver las pruebas unitarias que se han superado o han dado error en el Explorador de pruebas.
      
   ![Revisar los resultados de pruebas unitarias en el Explorador de pruebas](media/rununittest3.png) 

## <a name="view-live-unit-test-results"></a>Ver los resultados de las pruebas unitarias en vivo

Si está usando el marco de pruebas de MSTest, xUnit o NUnit en Visual Studio 2017 o versiones anteriores, puede ver los resultados en vivo de sus pruebas unitarias en la interfaz de usuario de Visual Studio.

1. Active las pruebas unitarias en vivo desde el menú **Prueba**.

   ![Activar las pruebas unitarias en vivo](media/live-test-results-start.png) 

1. Vea los resultados de las pruebas dentro de la ventana del editor de código a medida que escribe y edita el código.

   ![Señalar y hacer clic en los indicadores de resultados de la prueba](media/live-test-results-ui.png) 

1. Señale y haga clic en los indicadores de resultados de la prueba para ver más información.

   ![Ver los resultados de las pruebas](media/live-test-results-details.png) 

Para obtener más información, vea [Live Unit Testing en Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/live-unit-testing-visual-studio-2017-rc/).

<a name="intellitest"></a>
## <a name="generate-unit-tests-with-intellitest"></a>Generar pruebas unitarias con IntelliTest

Cuando ejecuta Intelltest, puede ver fácilmente qué pruebas son las que fallan y agregar cualquier código para corregirlas. Puede seleccionar las pruebas generadas que quiere guardar en un proyecto de prueba para proporcionar un conjunto de regresión. Cuando cambie el código, vuelva a ejecutar IntelliTest para mantener sincronizadas las pruebas generadas con los cambios de código. Para obtener información sobre cómo hacerlo, vea [Generar pruebas unitarias para el código con IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

![Generar pruebas unitarias con IntelliTest](media/intellitest.png)

<a name="unit-tests"></a>
## <a name="run-unit-tests-with-test-explorer"></a>Ejecutar pruebas unitarias con el Explorador de pruebas

Con el Explorador de pruebas puede ejecutar pruebas unitarias de Visual Studio o proyectos de prueba unitaria de terceros, agrupar pruebas en categorías, filtrar la lista de pruebas, y crear, guardar y ejecutar las listas de reproducción de pruebas. También puede depurar las pruebas, y analizar la cobertura de código y el rendimiento de la prueba. Para obtener información sobre cómo hacerlo, vea [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md).

![Ejecutar pruebas unitarias con el Explorador de pruebas](media/testexplorer.png)

<a name="code-coverage"></a>
## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Usar cobertura de código para determinar la cantidad de código que se está probando

Para determinar qué proporción de código del proyecto se está probando realmente mediante pruebas codificadas como pruebas unitarias, se puede utilizar la característica de cobertura de código de Visual Studio. Para restringir con eficacia los errores, las pruebas deberían ensayar o “cubrir” una proporción considerable del código. Para obtener información sobre cómo hacerlo, vea [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

![Usar cobertura de código para determinar la cantidad de código que se está probando](media/codecoverage.png)

## <a name="q--a"></a>Preguntas y respuestas

<!-- BEGINSECTION class="m-qanda" -->

<a name="frameworks"></a>
####P: ¿Puedo ejecutar pruebas unitarias en Visual Studio si uso otro marco de pruebas unitarias?

R: Sí, use el complemento para ese marco para que el ejecutor de pruebas de Visual Studio funcione con ese marco. Aquí se muestran algunos [complementos de marcos de pruebas unitarias para Visual Studio](http://go.microsoft.com/fwlink/?LinkID=246630).

1. Use el Administrador de extensiones de Visual Studio para descargar el complemento.
        
   ![Seleccionar complementos de pruebas unitarias de terceros con el Administrador de extensiones](media/install3rdpartyunittestframeworks1.png) 

1. Descargue el complemento de la Galería de Visual Studio desde Herramientas/Pruebas, o bien búsquelo si sabe el nombre.
        
   ![Descargar el complemento](media/install3rdpartyunittestframeworks2.png) 

1. Cree un proyecto de biblioteca de clases.
        
   ![Crear un proyecto de biblioteca de clases](media/create3rdpartyunittest1.png) 

   Agregue el proyecto a la solución.
    
   ![Asignar un nombre al proyecto de biblioteca de clases y agregarlo](media/create3rdpartyunittest3.png) 

1. En el proyecto de biblioteca de clases, ejecute NuGet para instalar el complemento.

   ![Administrar paquetes NuGet para instalar el complemento](media/create3rdpartyunittest3a.png) 

   [NuGet](https://www.nuget.org/) es una extensión de Visual Studio que puede usar para agregar y actualizar bibliotecas y herramientas para sus proyectos.

1. Instale el complemento. Si conoce el nombre, puede buscarlo en línea.

   ![Instalar el marco de terceros](media/create3rdpartyunittest4.png) 

   En el proyecto se hace referencia al marco.
        
   ![La referencia del marco de pruebas unitarias de terceros se agrega a la solución](media/create3rdpartyunittest6.png) 

1. En el proyecto de biblioteca de clases, agregue una referencia al proyecto que quiere probar.
        
   ![Agregar una referencia al proyecto](media/createunittest6.png) 

1. Seleccione el proyecto que contiene el código que va a probar.
        
   ![Seleccionar el proyecto de código que va a probar](media/createunittest7.png) 

1. Codifique la prueba unitaria.

   ![Agregar código a la prueba unitaria](media/create3rdpartyunittest7.png)   

<!-- ENDSECTION -->

## <a name="see-also"></a>Vea también

* [Crear un comando de pruebas unitarias](create-unit-tests-menu.md)
* [Generate tests with IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md) (Generar pruebas con IntelliTest)
* [Ejecutar pruebas con el Explorador de pruebas](run-unit-tests-with-test-explorer.md)
* [Determine code coverage](using-code-coverage-to-determine-how-much-code-is-being-tested.md) (Determinar la cobertura de código)
* [Mejorar la calidad del código](improve-code-quality.md)
