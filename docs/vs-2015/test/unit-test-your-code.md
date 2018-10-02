---
title: Haga una prueba unitaria de su código | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: gewarren
manager: douge
ms.openlocfilehash: a1c6c521e09795619af503e0a121e51f6edc33b9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578303"
---
# <a name="unit-test-your-code"></a>Haga una prueba unitaria de su código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [pruebas unitarias de código](https://docs.microsoft.com/visualstudio/test/unit-test-your-code).  
  
Las pruebas unitarias proporcionan a los desarrolladores y evaluadores una forma rápida de buscar errores lógicos en los métodos de clases de proyectos de [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] y [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)].  
  
 Las herramientas de pruebas unitarias incluyen:  
  
1.  **Explorador de pruebas.** El Explorador de pruebas permite ejecutar pruebas unitarias y ver los resultados. El Explorador de pruebas puede utilizar cualquier marco de pruebas unitarias, incluyendo un marco de terceros, que tiene un adaptador para el explorador.  
  
2.  **Marco de pruebas unitarias de Microsoft para código administrado.** El marco de pruebas unitarias de Microsoft para código administrado se instala con Visual Studio y proporciona un marco para probar el código .NET.  
  
3.  **Marco de pruebas unitarias de Microsoft para C++.** El marco de pruebas unitarias de Microsoft para C++ se instala con Visual Studio y proporciona un marco para probar código nativo.  
  
4.  **Herramientas de cobertura de código.** Puede determinar la cantidad de código de producto que utilizan las pruebas unitarias a partir de un comando en el Explorador de pruebas.  
  
5.  **Marco de aislamiento de Microsoft Fakes.** El marco de aislamiento de Microsoft Fakes puede crear clases y métodos de sustitución para el código de producción y de sistema que crean dependencias en el código en pruebas. Cuando se implementan falsos delegados para una función, se controla el comportamiento y el resultado del objeto de dependencia.  
  
 También puede crear pruebas [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md), que exploran el código .NET para generar datos de prueba y un conjunto de pruebas unitarias. Para cada instrucción en el código, se genera una entrada de prueba que ejecutará esa instrucción. Se lleva a cabo un análisis de caso para cada bifurcación condicional en el código.  
  
## <a name="key-tasks"></a>Tareas clave  
 Utilice los temas siguientes para facilitar la comprensión y la creación de pruebas unitarias:  
  
|Tareas|Temas relacionados|  
|-----------|-----------------------|  
|**Guías rápidas y tutoriales**: utilice los siguientes temas para aprender a hacer pruebas unitarias en Visual Studio a partir de ejemplos de código.|-   [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Inicio rápido: Desarrollo controlado por pruebas con el Explorador de pruebas](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Agregar pruebas unitarias a aplicaciones C++ existentes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Pruebas unitarias de código nativo con el Explorador de pruebas](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
|**Hacer pruebas unitarias con el Explorador de pruebas**: aprenda cómo el Explorador de pruebas puede ayudar a crear pruebas unitarias más productivas y eficaces.|-   [Conceptos básicos de las pruebas unitarias](../test/unit-test-basics.md)<br />-   [Crear un proyecto de prueba unitaria](../test/create-a-unit-test-project.md)<br />-   [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)<br />-   [Instalar marcos de prueba unitaria de terceros](../test/install-third-party-unit-test-frameworks.md)<br />-   [Actualizar pruebas unitarias desde Visual Studio 2010](http://msdn.microsoft.com/en-us/9bb75856-f68a-4de2-a084-b08a947a1172)|  
|**Pruebas unitarias de código administrado:**|-   [Escribir pruebas unitarias para .NET Framework con el Framework de pruebas unitarias de Microsoft para código administrado](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**Pruebas unitarias de código C++**|-   [Escribir pruebas unitarias para C/C++ con el marco de pruebas unitarias de Microsoft para C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**Aislamiento de pruebas unitarias**|-   [Aislar el código en pruebas con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**Utilizar cobertura de código para identificar qué proporción del código del proyecto se prueba utilizando pruebas unitarias:** obtenga información sobre la característica de cobertura de código de las herramientas de prueba de [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)].|-   [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**Realice análisis de esfuerzo y rendimiento usando pruebas de carga para las pruebas unitarias**: puede crear una prueba de carga y agregarle sus pruebas unitarias para ayudar a aislar los problemas de rendimiento y esfuerzo de la aplicación. **Nota:** La creación y el uso de pruebas de carga requiere Visual Studio Enterprise.|-   [Crear y editar pruebas de carga](http://msdn.microsoft.com/en-us/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Cómo: Agregar pruebas de rendimiento web y pruebas unitarias a un escenario de prueba de carga](http://msdn.microsoft.com/en-us/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Cómo: eliminar pruebas de web y pruebas unitarias desde un escenario de prueba de carga](http://msdn.microsoft.com/en-us/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|  
|**Establezca y exija puertas de calidad:** puede crear puertas de calidad para exigir que las pruebas se ejecuten antes de proteger el código para ayudar a garantizar la calidad del código.|-   [Establecer y aplicar pruebas de calidad](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Extienda el tipo de prueba unitaria:** puede agregar funcionalidad que no esté en el marco de pruebas unitarias. Por ejemplo, puede agregar una propiedad para especificar si una prueba se debe ejecutar como un usuario normal o no. O puede extender el marco para agregar atributos de fila a un método y utilizar los datos de esa fila dentro de la prueba.|Para ver ejemplos de código para extender el marco de pruebas unitarias, vea el siguiente [sitio web de Microsoft](http://go.microsoft.com/fwlink/?LinkId=185591).|  
|**Establecer opciones de prueba:** por ejemplo, puede especificar dónde se almacenan los resultados de las pruebas.|[Configurar pruebas unitarias mediante un archivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="related-tasks"></a>Tareas relacionadas  
 [Revisar los resultados de pruebas en Microsoft Test Manager](http://msdn.microsoft.com/en-us/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)  
  
 Describe los resultados de pruebas y las maneras de trabajar con ellos, incluidos como verlos, guardarlos y eliminarlos.  
  
 [Ejecutar pruebas del sistema mediante Microsoft Visual Studio](http://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)  
  
 Proporciona vínculos a información sobre cómo utilizar Visual Studio en oposición a utilizar [!INCLUDE[TCMext](../includes/tcmext-md.md)] para ejecutar las pruebas automatizadas.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Describe el espacio de nombres UnitTesting, que proporciona los atributos, excepciones, aserciones y otras clases que ofrecen compatibilidad para prueba unitaria.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 Describe el espacio de nombres UnitTesting.Web, que extiende el espacio de nombres UnitTesting proporcionando compatibilidad para [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] y pruebas unitarias de servicios Web.  
  
## <a name="external-resources"></a>Recursos externos  
  
### <a name="videos"></a>Vídeos  
 [Channel 9: Unit testing your Windows Store apps built using XAML (Channel 9: prueba de las unidades de las aplicaciones de la Tienda Windows compiladas mediante XAML)](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Foros  
 [Prueba unitaria de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="guidance"></a>Orientación  
 [Pruebas de entrega continua con Visual Studio 2012. Capítulo 2: Pruebas unitarias: Prueba del interior](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="reference"></a>Referencia  
 [Content Index for Unit Tests](http://go.microsoft.com/fwlink/?LinkID=254719) (Índice de contenido para las pruebas unitarias)  
  
## <a name="see-also"></a>Vea también  
 [Mejorar la calidad del código](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)   
 [Probar la aplicación](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)



