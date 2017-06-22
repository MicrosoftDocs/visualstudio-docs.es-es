---
title: Actualizar proyectos de prueba unitaria de Visual Studio 2010 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1502b51-d6db-4894-9fbf-4a5723e4bb1a
caps.latest.revision: 8
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: d6550f2aa1aab249eda569ff84ddf4dcf488aa18
ms.contentlocale: es-es
ms.lasthandoff: 05/13/2017

---
# <a name="upgrade-visual-studio-2010-unit-test-projects"></a>Actualizar proyectos de prueba unitaria de Visual Studio 2010
[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] incluye compatibilidad de proyecto de prueba con los proyectos de prueba de [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1. Por ejemplo, los proyectos de prueba creados con [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 se pueden abrir con [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] sin necesidad de actualizar. Por lo tanto, el equipo puede utilizar [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 y [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] para trabajar con el mismo proyecto de prueba. Para obtener más información, consulte [Actualizar pruebas unitarias desde Visual Studio 2010](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).  
  
 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] introduce varios cambios para las pruebas unitarias. Debido a estos cambios, es importante comprender los problemas de compatibilidad entre versiones anteriores de Visual Studio y [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. De entre los cambios a las pruebas unitarias, uno importante es que [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] incluye más de una plantilla de proyecto de prueba, incluyendo una plantilla de proyecto de prueba unitaria. Las pruebas unitarias nuevas se agregan a la nueva plantilla de proyecto de prueba unitaria. Las pruebas unitarias también pueden incluirse en otra plantilla de proyecto de prueba nueva denominada plantilla de proyecto de prueba de IU codificada. Para obtener más información sobre las nuevas plantillas de proyectos de prueba, consulte [Actualizar pruebas de versiones anteriores de Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52). Los nuevos proyectos de prueba unitaria ya no incluyen un archivo de configuración de pruebas de forma predeterminada. Si se excluye el archivo de configuración de pruebas, se mejora el rendimiento de las pruebas unitarias. Para la compatibilidad, aún puede usar los proyectos de prueba existentes creados con Visual Studio 2010. Sin embargo, se recomienda que quite el archivo de configuración asociado al proyecto de prueba por motivos de rendimiento, a menos que necesite específicamente el archivo de configuración de pruebas. Por ejemplo, puede conservar el archivo de configuración de pruebas si las pruebas unitarias se ejecutan en un entorno distribuido o si necesita recopilar datos de diagnóstico específicos. Si tiene una necesidad similar con la nueva plantilla de proyecto de prueba unitaria o la plantilla de proyecto de pruebas de IU codificadas, también puede agregarles manualmente un archivo de configuración de pruebas.  
  
> [!NOTE]
>  Las pruebas unitarias existentes en los proyectos de prueba de [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 funcionarán sin problemas entre [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 y [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. No se realizan cambios a los archivos de proyecto de prueba cuando se abre un proyecto de prueba de Visual Studio 2010 que contiene las pruebas unitarias en [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], o viceversa.  
  
> [!CAUTION]
>  Visual Studio 2010 no puede abrir proyectos de C + + / CLI cuyo destino sea el conjunto de herramientas 11.0, es decir, proyectos creados en Visual Studio 2012. Esta restricción no solo se aplica a los proyectos de prueba unitaria de C++/CLI, sino también a todos los proyectos de C++ /CLI.  
  
> [!NOTE]
>  Puede ejecutar las nuevas pruebas unitarias usando vstest.console.exe desde la línea de comandos. Para obtener más información sobre el uso de vstest.console.exe, consulte [Opciones de línea de comandos de VSTest.Console.exe](/devops-test-docs/test/vstest-console-exe-command-line-options), o ejecute el comando mediante el modificador de ayuda: **vstest.console.exe /?**. Aún puede ejecutar las pruebas unitarias existentes mediante MStest.exe. Para obtener más información, consulte[Ejecutar pruebas automatizadas desde la línea de comandos usando MSTest](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest) y [Opciones de la línea de comandos para MSTest.exe](/devops-test-docs/test/mstest-exe-command-line-options).  
  
 Otro cambio importante es el nuevo Explorador de pruebas. En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], algunas de las ventanas de pruebas con que puede conocer de versiones anteriores de Visual Studio han quedado en desuso, como por ejemplo la ventana Vista de pruebas. El Explorador de pruebas está diseñado para dar mejor soporte a los desarrolladores y a los equipos que incorporan las pruebas unitarias en sus prácticas de desarrollo de software. Para obtener más información, consulte [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md).  
  
## <a name="compatibility-issues-between-visual-studio-2010-sp1-and-visual-studio-2012"></a>Problemas de compatibilidad entre Visual Studio 2010 SP1 y Visual Studio 2012  
 Estos son algunos problemas que debe tener en cuenta al migrar pruebas unitarias entre Visual Studio 2010 SP1 y [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]:  
  
|Funcionalidad de pruebas unitarias|Problema|Soluciones|  
|-----------------------------|-----------|--------------|  
|Las listas de pruebas (archivos .vsmdi) están en desuso en [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|Ya no podrá crear nuevas listas de pruebas (archivos .vsmdi) o ejecutar listas de pruebas desde Visual Studio. **Consejo:**  Las categorías de prueba proporcionan más flexibilidad que la funcionalidad de listas de pruebas de las versiones anteriores de Microsoft Visual Studio. Puede usar operadores lógicos con las categorías de pruebas para ejecutar pruebas de varias categorías juntas o establecer que se ejecuten pruebas que pertenecen a varias categorías. Asimismo, las categorías de pruebas son fáciles de agregar cuando se crean los métodos de prueba y no es necesario mantener listas de pruebas después de haber creado los métodos de prueba. Con las categorías de pruebas, no es necesario insertar en el repositorio y extraer del repositorio el archivo **\<nombre de la solución>.vsmdi** que mantiene las listas de pruebas. Para obtener más información, consulte [Definir categorías de pruebas para agrupar las pruebas](/devops-test-docs/test/defining-test-categories-to-group-your-tests).|-   Para mantener la compatibilidad con los proyectos de prueba existentes que utilizan listas de pruebas, todavía puede editar los archivos .vsmdi con Visual Studio.<br />-   Aunque no se pueden ejecutar listas de pruebas migradas con Visual Studio, todavía puede ejecutarlas usando mstest.exe desde la línea de comandos. Parea obtener más información, consulte [Cómo: Ejecutar pruebas automatizadas desde la línea de comandos usando MSTest](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest)<br />-   Si utiliza una lista de pruebas en su definición de compilación, puede continuar utilizándola. Para obtener más información, consulte [Cómo: Configurar y ejecutar pruebas programadas después de compilar la aplicación](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd) y [Ejecutar pruebas en el proceso de compilación](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38).|  
|Los descriptores de acceso privados están en desuso en [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].<br /><br /> En versiones anteriores de Visual Studio, puede usar Publicize para especificar interfaces de programación de aplicaciones (API) internas y crear una API pública equivalente que puede llamar en las pruebas, la cual a su vez llamará a las API internas de su producto. Después puede utilizar la generación de código para crear clases stub para pruebas y generar el fragmento de código dentro de ese stub.|Ya no podrá crear descriptores de acceso privados.|<ul><li>Los proyectos de prueba de Visual Studio 2010 se compilarán y funcionarán en [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. La compilación incluirá advertencias de salida.</li><li>Si desea probar las API internas, tienes estas opciones:<br /><br /> <ul><li>Use la clase <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> para ayudar a obtener acceso a las API internas y privadas a su código. Puede encontrarla en el ensamblado Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll.</li><li>Cree un marco de reflexión que sea capaz de reflejar su código para tener acceso a las API internas o privadas.</li><li>Si el código al que está intentando tener acceso es interno, quizás pueda acceder a las API usando <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para que el código de prueba pueda tener acceso a las API internas.</li></ul></li></ul>|  
|Se elimina el impacto en las pruebas|||  
|Uso compartido de los resultados de la ejecución a través de los registros TRX desde el Explorador de pruebas.||Todavía puede obtener los registros TRX desde la línea de comandos y Team Build.|  
  
## <a name="see-also"></a>Vea también  
 [Portar, migrar y actualizar proyectos de Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [Hacer una prueba unitaria de su código](../test/unit-test-your-code.md)   
 [Actualizar pruebas de versiones anteriores de Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [Actualizar pruebas de IU codificadas desde Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)

