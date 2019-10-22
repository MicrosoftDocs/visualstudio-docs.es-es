---
title: Opciones, editor de texto, C-C++, avanzado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 236135cd4b4f813471ece7a0eeb1b221c7242df9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662364"
---
# <a name="options-text-editor-cc-advanced"></a>Opciones, editor de texto, C/C++, avanzado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Al cambiar estas opciones, puede modificar el comportamiento relacionado con IntelliSense y la base de datos de exploración cuando programa en C o C++.

 Para tener acceso a esta página, en el cuadro de diálogo **Opciones**, en el panel izquierdo, expanda **Editor de texto**, expanda **C/C++** y, después, pulse **Opciones avanzadas**.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Vea [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Exploración o navegación
 Nunca debería elegir estas opciones excepto en el caso excepcional donde una solución sea tan grande que la actividad de base de datos use una cantidad inaceptable de recursos del sistema.

 **Deshabilitar base de datos** Todo el uso de la base de datos de exploración de código (SDF), todas las demás opciones de exploración y navegación, y todas las características de IntelliSense, excepto #include Autocompletar, están deshabilitadas.

 **Deshabilitar actualizaciones de base de datos** La base de datos se abrirá como de solo lectura y no se realizará ninguna actualización a medida que se modifiquen los archivos. La mayoría de las características seguirán funcionando. En cambio, cuando se realicen las modificaciones, los datos quedarán obsoletos y obtendrá resultados incorrectos.

 **Deshabilitar actualizaciones automáticas de bases de datos** La base de datos de exploración de código no se actualizará automáticamente cuando se modifiquen los archivos de código fuente. En cambio, si abre el **Explorador de soluciones**, abre el menú contextual del proyecto y, después, pulsa **Volver a examinar la solución**, todos los archivos obsoletos se comprobarán y la base de datos se actualizará.

 **Deshabilitar archivos implícitos** La base de datos de exploración de código no recopila datos de archivos que no se especifican en un proyecto. Un proyecto contiene archivos de origen y archivos de encabezado que se especifican explícitamente. Los archivos implícitos se incluyen mediante archivos explícitos (por ejemplo, afxwin.h, windows.h y atlbase.h). Normalmente, el sistema busca estos archivos y también los indexa para diferentes características de exploración (incluida Navegar a). Si elige esta opción, esos archivos no se indexan y algunas características no están disponibles para ellos. Si elige esta opción, "Deshabilitar limpieza implícita" y "Deshabilitar carpetas de dependencias externas" también se eligen de manera implícita.

 **Deshabilitar limpieza implícita** La base de datos de exploración de código no limpia los archivos implícitos a los que ya no se hace referencia. Esta opción impide que los archivos implícitos se quiten de la base de datos cuando ya no se usan. Por ejemplo, si agrega una directiva `#include` que hace referencia a mapi.h en uno de los archivos de origen, mapi.h se encontrará e indexará. Si después quita #include y no se hace referencia al archivo en ningún lugar, la información sobre este se quitará finalmente a menos que elija esta opción. (Consulte la opción **intervalo de solución de volver a examinar** ). Esta opción se omite cuando se vuelve a examinar explícitamente la solución.

 **Deshabilitar carpetas de dependencias externas** No se crea ni actualiza la carpeta dependencias externas de cada proyecto. En el **Explorador de soluciones**, cada proyecto contiene una carpeta de dependencias externas, que contiene todos los archivos implícitos de ese proyecto. Si elige esta opción, esa carpeta no aparece.

 **Volver a crear base de datos** Vuelva a crear la base de datos de exploración de código desde cero la próxima vez que se cargue la solución. Si elige esta opción, el archivo de base de datos SDF se elimina la próxima vez que cargue la solución, por lo que la base de datos se volverá a crear y todos los archivos se indexarán.

 **Volver a examinar el intervalo** de la solución Un trabajo "volver a examinar solución ahora" está programado para el intervalo que especifique. Debe especificar un valor entre 0 y 5000 minutos. El valor predeterminado es de 60 minutos. Mientras la solución se vuelve a examinar, las marcas de tiempo de archivo se comprueban para determinar si un archivo se ha cambiado fuera del IDE. (Se realiza un seguimiento automático de los cambios realizados en el IDE y se actualizan los archivos). Los archivos incluidos implícitamente se comprueban para determinar si todavía se hace referencia a ellos.

## <a name="diagnostic-logging"></a>Registro de diagnóstico
 Estas opciones se proporcionan en caso de que Microsoft le pida recopilar información avanzada para diagnosticar un problema. La información de registro no es útil para los usuarios y recomendamos que la mantenga deshabilitada.

 **Habilitar registro** Habilita el registro de diagnóstico en la ventana de salida.

 **Nivel de registro** Establezca el nivel de detalle del registro, de 0 a 5.

 **Filtro de registro** Los filtros muestran tipos de evento mediante una máscara de máscara.

 Puede establecerlo con una suma de alguna de las siguientes opciones:

- 0 - Ninguno

- 1 - General

- 2 - Inactivo

- 4 - WorkItem

- 8 - IntelliSense

- 16 - ACPerf

- 32 - ClassView

## <a name="fallback-location"></a>Ubicación de recursos de reserva
 La ubicación de recursos de reserva es el lugar donde se colocan los archivos auxiliares de SDF e IntelliSense (por ejemplo, iPCH) cuando la ubicación principal (mismo directorio que la solución) no se usa. Esta situación puede producirse si el usuario no tiene permisos para escribir en el directorio de la solución o este se encuentra en un dispositivo lento. La ubicación de recursos de reserva predeterminada está en el directorio temporal del usuario.

 **Usar siempre ubicación de reserva** Indica que la base de datos de exploración de código y los archivos de IntelliSense deben almacenarse siempre en una carpeta que especifique como la "ubicación de reserva", no junto al archivo. sln. El IDE nunca intentará colocar los archivos SDF o iPCH junto al directorio de la solución y siempre usará la ubicación de recursos de reserva.

 **No advertir si se usa la ubicación de reserva** No está informado o se le pregunta si se usa una "ubicación de reserva". Normalmente, el IDE le indicará si tuvo que usar la ubicación de recursos de reserva. Esta opción desactiva esa advertencia.

 **Ubicación de reserva** Este valor se usa como ubicación secundaria para almacenar la base de datos de exploración de código o los archivos de IntelliSense. De manera predeterminada, el directorio temporal es su ubicación de recursos de reserva. El IDE creará un subdirectorio en la ruta especificada (o el directorio temporal) que incluye el nombre de la solución junto con un hash de la ruta de acceso completa a la solución, lo que evita problemas con nombres de solución que son idénticos.

## <a name="intellisense"></a>IntelliSense
 **Información rápida automática** Habilita la información sobre herramientas de QuickInfo cuando se mueve el puntero sobre el texto.

 **Deshabilitar IntelliSense** Deshabilita todas las características de IntelliSense. El IDE no crea procesos VCPkgSrv.exe para atender las solicitudes de IntelliSense, y ninguna característica de IntelliSense funcionará (Información rápida, Lista de miembros, Autocompletar, Ayuda de Parám). La coloración semántica y el resaltado de referencias también están deshabilitados. Esta opción no deshabilita las características de exploración que se basan únicamente en la base de datos (incluida la barra de navegación, ClassView y la ventana Propiedades).

 **Deshabilitar actualización automática** La actualización de IntelliSense se retrasa hasta que se realiza una solicitud real de IntelliSense. Este retraso puede provocar un tiempo de ejecución mayor de la primera operación de IntelliSense en un archivo, pero puede resultar útil para establecer esta opción en equipos con recursos limitados o muy lentos. Si elige esta opción, también elige implícitamente las opciones "Deshabilitar informe de errores" y "Deshabilitar subrayados ondulados".

 **Deshabilitar informes de errores** Deshabilita los informes de errores de IntelliSense a través de subrayados ondulados y la ventana Lista de errores. También deshabilita el análisis en segundo plano asociado con los informes de errores. Si elige esta opción, también elige implícitamente la opción "Deshabilitar subrayados ondulados".

 **Deshabilitar Garabatos** Deshabilita los subrayados ondulados de error de IntelliSense. Los "subrayados ondulados" rojos no se muestran en la ventana del editor, pero el error seguirá apareciendo en la ventana Lista de errores.

 **Deshabilitar #include Autocompletar** Deshabilita la finalización automática de instrucciones `#include`.

 **Usar barra diagonal en #include Autocompletar** Desencadena la finalización automática de instrucciones `#include` cuando se utiliza "/". El delimitador predeterminado es la barra diagonal inversa "\". El compilador puede aceptar cualquiera, por lo que use esta opción para especificar la que usa su código base.

 **Unidades de traducción máximas almacenadas en caché** Número máximo de unidades de traducción que se mantendrán activas al mismo tiempo para solicitudes de IntelliSense. Debe especificar un valor entre 2 y 15. Este número se relaciona directamente con el número máximo de procesos VCPkgSrv.exe que se ejecutarán (para una instancia determinada de Visual Studio). El valor predeterminado es 2, pero si tiene memoria disponible, puede aumentar este valor y posiblemente conseguir un rendimiento ligeramente mejor en IntelliSense.

 Para obtener más información sobre unidades de traducción, vea [Fases de traducción](https://msdn.microsoft.com/library/a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db).

 **Deshabilitar la lista de miembros agresiva** La lista de miembros no aparece mientras escribe el nombre de un tipo o una variable. La lista aparece solo después de que escriba uno de los caracteres de confirmación, según lo definido en la opción **Caracteres de confirmación de las listas de miembros**.

 **Deshabilitar palabras clave de lista de miembros** Las palabras clave del lenguaje como `void`, `class` `switch` no aparecen en las sugerencias de la lista de miembros.

 **Deshabilitar fragmentos de código de lista de miembros** Los fragmentos de código no aparecen en las sugerencias de la lista de miembros.

 **Deshabilitar coloración semántica** Desactiva toda la coloración del código, excepto las palabras clave, las cadenas y los comentarios del lenguaje.

 **Confirmación de la lista de miembros inteligentes** Agrega una línea cuando se elige la tecla entrar al final de una palabra totalmente escrita.

 **Modo de filtro de lista de miembros** Establece el tipo de algoritmo de coincidencia. **Aproximada** busca las coincidencias más posibles porque usa un algoritmo que es similar a un corrector ortográfico para buscar coincidencias que sean similares pero no idénticas. **Filtrado inteligente** coincide con subcadenas incluso si no se encuentran al comienzo de una palabra. **Prefijo** solo coincide con subcadenas idénticas que comienzan al principio de la palabra.

 **Caracteres de confirmación** de la lista de miembros Especifica los caracteres que provocan la confirmación de la sugerencia de lista de miembros resaltada actualmente. Puede agregar o quitar caracteres de esta lista.

## <a name="references"></a>Referencias
 **Deshabilitar resolución** Por motivos de rendimiento, en "Buscar todas las referencias" se muestran los resultados de la búsqueda de texto sin formato de forma predeterminada en lugar de usar IntelliSense para comprobar cada candidato. Puede desactivar esta casilla para obtener resultados más precisos en todas las operaciones de búsqueda. Para filtrar en una base por búsqueda, abra el menú contextual para obtener la lista de resultados y, después, pulse "Resolver resultados".

 **Ocultar sin confirmar** Ocultar elementos no confirmados en los resultados de "Buscar todas las referencias". Si no establece la opción "Deshabilitar resolución", puede usar esta opción para ocultar los elementos no confirmados en los resultados.

 **Deshabilitar resaltado de referencia**

## <a name="see-also"></a>Vea también
 [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)
