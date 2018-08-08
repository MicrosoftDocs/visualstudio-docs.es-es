---
title: Importar un proyecto XCode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 074128d34f88346708fd344d1bba25b833f2af44
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251567"
---
# <a name="import-an-xcode-project"></a>Importar un proyecto XCode
Microsoft Visual C++ para desarrollo móvil multiplataforma incluye compatibilidad para mover los proyectos de XCode a Visual Studio, donde puede crear bibliotecas multiplataforma y compartir código con otros proyectos. El asistente Importar de XCode simplifica el proceso de importación de proyectos y de división del código de C++ en los destinos de XCode para usarlo como una biblioteca estática o un proyecto de código compartido. Puede administrar el código específico de iOS en Visual Studio y seguir usando XCode para realizar guiones gráficos y compilaciones. Para obtener información sobre cómo mover fácilmente código entre Visual Studio y XCode, y viceversa, vea Mover cambios entre XCode y Visual Studio.  
  
## <a name="use-the-import-from-xcode-wizard"></a>Uso del asistente Importar de XCode  
 En este tema se muestra cómo mover un proyecto de XCode a Visual Studio para aprovechar las soluciones multiplataforma y el uso compartido del código. Como requisito previo, debe emparejar su Mac a Visual Studio para poder importar, exportar y compilar el proyecto. Para obtener instrucciones sobre cómo configurar el emparejamiento, vea [Instalar y configurar herramientas para compilar con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). También debe compartir el proyecto de XCode en la red o moverlo a su equipo de Visual Studio para usar el asistente Importar de XCode.  
  
#### <a name="import-from-xcode"></a>Importar desde XCode  
  
1.  En el menú **Archivo**, seleccione **Nuevo**, **Importar**, **Importar de XCode**. Esto inicia el cuadro de diálogo del asistente **Importar de XCode**.  
  
     ![Elija el proyecto de destino de XCode para importar](../cross-platform/media/cppmdd_u2_importxcode_choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2.  En el panel **Elegir un proyecto**, haga clic en el botón Examinar para seleccionar un archivo *.pbxproj* de XCode. Desplácese hasta el archivo de proyecto en el cuadro de diálogo **Seleccionar archivo del proyecto XCode** y después pulse **Abrir**.  
  
     ![Seleccione un archivo de proyecto en el cuadro de diálogo Seleccionar archivo del proyecto XCode](../cross-platform/media/cppmdd_u2_importxcode_browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
     En el asistente Importar de XCode, pulse **Siguiente**.  
  
3.  En el panel **Destinos**, elija los destinos del proyecto de XCode para importar en proyectos de Visual Studio. Los destinos de XCode son similares a los proyectos de Visual Studio. La mayoría son una colección de código y recursos que generan un archivo binario. El asistente Importar de XCode solo permite la importación de destinos que generan un archivo binario, pero no una biblioteca estática, como destinos. Los destinos de biblioteca estática de XCode son el asunto del siguiente paso.  
  
     ![Importar desde el panel Destinos del Asistente de XCode](../cross-platform/media/cppmdd_u2_importxcode_destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
     Para cada destino seleccionado en **Destinos para importar**, el asistente detecta automáticamente los archivos de código de C++ que se pueden dividir en un proyecto de biblioteca estática independiente y los coloca en la sección **Elementos del proyecto de C++**. En la sección **Elementos del proyecto de C++** se mantiene código y recursos adicionales. Se convierten en objetos independientes de biblioteca estática y proyectos de aplicación en Visual Studio cuando el asistente finaliza el proceso de importación. De forma predeterminada, el asistente no divide los destinos de prueba unitaria y marco en proyectos independientes.  
  
     Para cambiar los archivos que están en cada proyecto, use los botones Arriba y Abajo. Cuando esté satisfecho con los archivos de cada proyecto, pulse **Siguiente** para continuar.  
  
4.  En el panel **Destinos de biblioteca**, elija los destinos de biblioteca estática de XCode para importar en proyectos de Visual Studio. En este panel, puede elegir qué archivos se colocan en un proyecto de código compartido y cuáles se colocan en un proyecto de biblioteca estática. En cada uno de los destinos de la lista **Destinos para importar**, puede controlar los archivos que se colocan en **Elementos del proyecto de código compartido** y **Elementos del proyecto de biblioteca estática** mediante los botones Arriba y Abajo.  
  
     ![Importar desde el panel Destinos de biblioteca de XCode](../cross-platform/media/cppmdd_u2_importxcode_library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
     Un proyecto de código compartido es una manera de compartir un conjunto de archivos de código fuente entre proyectos en Visual Studio. El código se compila como parte del proyecto que lo incluye, no como un proyecto propio. Dado que los proyectos que incluyen el código compartido pueden tener configuraciones y arquitecturas diferentes, esta es la mejor manera de proporcionar un único proyecto que contiene código que se puede compilar para muchos tipos de plataformas.  
  
     Cuando esté satisfecho con los archivos de cada proyecto, pulse **Siguiente** para continuar.  
  
5.  El panel **Propiedades globales** se puede usar para establecer una ruta de búsqueda de marco y una ruta de búsqueda de encabezado de inclusión para todos los proyectos de iOS en Visual Studio. Visual Studio usa estas rutas para la exploración de código fuente y para IntelliSense. Estas rutas de acceso globales son útiles al crear proyectos de iOS que usan un conjunto común de encabezados y marcos.  
  
     ![Importar desde el panel Propiedades globales de XCode](../cross-platform/media/cppmdd_u2_importxcode_global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
     Estas rutas de acceso globales también pueden establecerse en Visual Studio en el cuadro de diálogo **Opciones**. Para encontrarlas, elija **Opciones** en el menú **Herramientas**. En el cuadro de diálogo **Opciones**, expanda **Multiplataforma**, **C++**, **iOS**, **Propiedades globales**.  
  
     Elija **Siguiente** para continuar.  
  
6.  El panel **Marcos** se usa para configurar las rutas de acceso que Visual Studio utiliza para examinar e IntelliSense para el proyecto. Las rutas de acceso deben ser accesibles para Visual Studio para cada marco al que hace referencia el proyecto de XCode. El asistente comprueba las referencias de marco en los proyectos XCode y muestra si puede encontrar el marco. Cualquier ruta de acceso ya configurada en las propiedades globales debe ser detectada por Visual Studio. Las excepciones se muestran en la lista Marcos. Para cada marco indicado con una X, proporcione una ruta accesible de PC para que Visual Studio busque el marco. Puede usar el botón Examinar **...** para usar un cuadro de diálogo **Seleccionar carpeta** para buscar la ruta de acceso. La ruta de acceso del marco puede ser una copia local o un recurso compartido accesible a través de una red en su Mac.  
  
     ![Importar desde el panel Marcos de XCode](../cross-platform/media/cppmdd_u2_importxcode_frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
     Elija **Siguiente** para continuar.  
  
7.  El panel **Configuración del proyecto** le permite cambiar la configuración de ruta de búsqueda de marcos y encabezados de inclusión para cada proyecto que crea el asistente. Use este panel para establecer rutas de acceso específicas del proyecto que difieran de la configuración global.  
  
     Para establecer una ruta de acceso para un proyecto específico, en el menú desplegable **Proyecto de destino**, seleccione el archivo de proyecto y después establezca los valores en los controles **Ruta de búsqueda de marco** e **Incluir la ruta de búsqueda de encabezado**. Puede usar el botón Examinar **...** junto a cada control para usar un cuadro de diálogo **Seleccionar carpeta** para buscar la ruta de acceso.  
  
     ![Importar desde el panel Proyectos de XCode](../cross-platform/media/cppmdd_u2_importxcode_projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
     Si no se emparejó ningún equipo Mac con este PC en Visual Studio, se muestra el vínculo **Configurar una máquina remota**. Para obtener instrucciones sobre cómo configurar el emparejamiento, vea [Instalar y configurar herramientas para compilar con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
     Para importar el proyecto de XCode mediante la configuración del asistente, haga clic en **Importar**.  
  
 El asistente Importar de XCode crea proyectos en Visual Studio que se corresponden con los destinos de proyecto de XCode seleccionados. El código que puede compartirse con otros proyectos de C++ se divide en proyectos independientes de código compartido y de biblioteca estática. El código restante se coloca en proyectos de biblioteca y aplicación de iOS que Visual Studio puede compilar de forma remota. Para obtener más información sobre cómo mover código entre Visual Studio y XCode, vea [Sincronizar cambios entre XCode y Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).