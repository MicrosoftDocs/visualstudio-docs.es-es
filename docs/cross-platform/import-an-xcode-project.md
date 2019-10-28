---
title: Importación de un proyecto de Xcode | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 62161b612d6c4583cd2206c3d18dc6606d2d9f0b
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588890"
---
# <a name="import-an-xcode-project"></a>Importación de un proyecto de Xcode

Las herramientas de Visual Studio para el desarrollo móvil multiplataforma con C++ incluyen compatibilidad para mover los proyectos de Xcode a Visual Studio, donde puede crear bibliotecas multiplataforma y compartir código con otros proyectos. El asistente Importar de Xcode simplifica el proceso de importación de proyectos y de división del código de C++ en los destinos de Xcode para usarlo como una biblioteca estática o un proyecto de código compartido. Puede administrar el código específico de iOS en Visual Studio y seguir usando Xcode para realizar guiones gráficos y compilaciones. Para obtener información sobre cómo mover fácilmente código entre Visual Studio y Xcode, y viceversa, vea [Sincronizar cambios entre Xcode y Visual Studio](sync-changes-between-xcode-and-visual-studio.md).

## <a name="use-the-import-from-xcode-wizard"></a>Uso del asistente Importar de Xcode

En este artículo se muestra cómo mover un proyecto de Xcode a Visual Studio para aprovechar las soluciones multiplataforma y el uso compartido del código. Como requisito previo, debe emparejar su Mac con Visual Studio para importar, exportar y compilar el proyecto. Para obtener instrucciones sobre cómo configurar el emparejamiento, vea [Instalar y configurar herramientas para compilar con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). También debe compartir el proyecto de Xcode en la red o moverlo a su equipo de Visual Studio para usar el asistente Importar de Xcode.

### <a name="import-from-xcode"></a>Importar de Xcode

1. En el menú **Archivo**, seleccione **Nuevo**, **Importar**, **Importar de Xcode**. Este comando inicia el cuadro de diálogo del asistente **Importar de Xcode**.

   ![Elegir el proyecto de destino de Xcode para importar](../cross-platform/media/cppmdd_u2_importxcode_choose.PNG "Elegir el proyecto de destino de Xcode para importar")

1. En el panel **Elegir un proyecto**, haga clic en el botón Examinar para seleccionar un archivo *.pbxproj* de Xcode. Desplácese hasta el archivo de proyecto en el cuadro de diálogo **Seleccionar archivo del proyecto Xcode** y después elija **Abrir**.

   ![Seleccionar un archivo de proyecto en el cuadro de diálogo Seleccionar archivo del proyecto Xcode](../cross-platform/media/cppmdd_u2_importxcode_browse.PNG "Seleccionar un archivo de proyecto en el cuadro de diálogo Seleccionar archivo del proyecto Xcode")

   En el asistente Importar de Xcode, elija **Siguiente**.

1. En el panel **Objetivos de destino**, elija los destinos del proyecto de Xcode para importar en proyectos de Visual Studio. Los destinos de Xcode son similares a los proyectos de Visual Studio. La mayoría son una colección de código y recursos que generan un archivo binario. El asistente Importar de Xcode solo permite la importación de destinos que generan un archivo binario, pero no una biblioteca estática, como destinos. Los destinos de biblioteca estática de Xcode son el asunto del siguiente paso.

   ![Importar desde el panel destinos de destino del asistente de Xcode](../cross-platform/media/cppmdd_u2_importxcode_destination.jpg "Importar desde el panel destinos de destino del asistente de Xcode")

   Para cada destino seleccionado en **Destinos para importar**, el asistente detecta automáticamente los archivos de código de C++ que se pueden dividir en un proyecto de biblioteca estática independiente y los coloca en la sección **Elementos del proyecto de C++** . En la sección **Elementos del proyecto de Xcode** se mantiene código y recursos adicionales. Se convierten en objetos independientes de biblioteca estática y proyectos de aplicación en Visual Studio cuando el asistente finaliza el proceso de importación. De forma predeterminada, el asistente no divide los destinos de prueba unitaria y marco en proyectos independientes.

   Para cambiar los archivos que están en cada proyecto, use los botones Arriba y Abajo. Cuando esté satisfecho con los archivos de cada proyecto, elija **Siguiente** para continuar.

1. En el panel **Objetivos de biblioteca**, elija los destinos de biblioteca estática de Xcode para importar en proyectos de Visual Studio. En este panel, puede elegir qué archivos se colocan en un proyecto de código compartido y cuáles se colocan en un proyecto de biblioteca estática. En cada uno de los destinos de la lista **Targets to import** (Destinos para importar), puede controlar los archivos que se colocan en **Shared Code project items** (Elementos del proyecto de código compartido) y **Static Library project items** (Elementos del proyecto de biblioteca estática) mediante los botones Arriba y Abajo.

   ![Importar desde el panel Objetivos de biblioteca de Xcode](../cross-platform/media/cppmdd_u2_importxcode_library.jpg "Importar desde el panel Objetivos de biblioteca de Xcode")

   Un proyecto de código compartido es una manera de compartir un conjunto de archivos de código fuente entre proyectos en Visual Studio. El código se compila como parte del proyecto que lo incluye, no como un proyecto propio. Los proyectos que incluyen el código compartido pueden tener diferentes arquitecturas y configuraciones. Un proyecto de código compartido es la mejor manera de proporcionar un proyecto único que contiene código que se puede compilar para muchos tipos de plataformas.

   Cuando esté satisfecho con los archivos de cada proyecto, elija **Siguiente** para continuar.

1. Use el panel **Propiedades globales** para establecer una ruta de búsqueda de marco y una ruta de búsqueda de encabezado de inclusión para todos los proyectos de iOS en Visual Studio. Visual Studio usa estas rutas para la exploración de código fuente y para IntelliSense. Estas rutas de acceso globales son útiles al crear proyectos de iOS que usan un conjunto común de encabezados y marcos.

   ![Importar desde el panel Propiedades globales de Xcode](../cross-platform/media/cppmdd_u2_importxcode_global.jpg "Importar desde el panel Propiedades globales de Xcode")

   Estas rutas de acceso globales también pueden establecerse en Visual Studio en el cuadro de diálogo **Opciones**. Para encontrarlas, elija **Opciones** en el menú **Herramientas**. En el cuadro de diálogo **Opciones**, expanda **Multiplataforma** > **C++**  > **iOS** > **Propiedades globales**.

   Elija **Siguiente** para continuar.

1. El panel **Marcos** se usa para configurar las rutas de acceso que Visual Studio utiliza para examinar e IntelliSense para el proyecto. Las rutas de acceso deben ser accesibles para Visual Studio para cada marco al que hace referencia el proyecto de Xcode. El asistente comprueba las referencias de marco en los proyectos Xcode y muestra si Visual Studio puede encontrar el marco. Cualquier ruta de acceso ya configurada en las propiedades globales debe ser detectada por Visual Studio. Las excepciones se muestran en la lista Marcos. Para cada marco indicado con una X, proporcione una ruta accesible de PC para que Visual Studio busque el marco. Puede usar el botón Examinar **...** para usar un cuadro de diálogo **Seleccionar carpeta** para buscar la ruta de acceso. La ruta de acceso del marco puede ser una copia local o un recurso compartido accesible a través de una red en su Mac.

   ![Importar desde el panel Marcos de Xcode](../cross-platform/media/cppmdd_u2_importxcode_frameworks.jpg "Importar desde el panel Marcos de Xcode")

   Elija **Siguiente** para continuar.

1. El panel **Configuración del proyecto** le permite cambiar la configuración de ruta de búsqueda de marcos y encabezados de inclusión para cada proyecto que crea el asistente. Use este panel para establecer rutas de acceso específicas del proyecto que difieran de la configuración global.

   Para establecer una ruta de acceso para un proyecto específico, en la lista desplegable **Proyecto de destino**, seleccione el archivo de proyecto. A continuación, establezca los valores en los controles **Ruta de búsqueda de marco** e **Incluir la ruta de búsqueda de encabezado**. Puede usar el botón Examinar **...** junto a cada control para usar un cuadro de diálogo **Seleccionar carpeta** para buscar la ruta de acceso.

   ![Importar desde el panel Proyectos de Xcode](../cross-platform/media/cppmdd_u2_importxcode_projects.jpg "Importar desde el panel Proyectos de Xcode")

   Si no se emparejó ningún equipo Mac con este PC en Visual Studio, se muestra el vínculo **Configurar una máquina remota**. Para obtener instrucciones sobre cómo configurar el emparejamiento, vea [Instalar y configurar herramientas para compilar con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

   Para importar el proyecto de Xcode mediante la configuración del asistente, haga clic en **Importar**.

   El asistente Importar de Xcode crea proyectos en Visual Studio que se corresponden con los destinos de proyecto de Xcode seleccionados. El código que puede compartirse con otros proyectos de C++ se divide en proyectos independientes de código compartido y de biblioteca estática. El código restante se coloca en proyectos de biblioteca y aplicación de iOS que Visual Studio puede compilar de forma remota. Para más información sobre cómo mover código entre Visual Studio y Xcode, vea [Sincronizar cambios entre Xcode y Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Instalación del desarrollo móvil multiplataforma con C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
