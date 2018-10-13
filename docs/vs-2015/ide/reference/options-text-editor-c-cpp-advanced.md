---
title: Opciones, Editor de texto, C/C ++, avanzado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aafa46e62af6eadb56d8cf53cb2190bc7403358b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285706"
---
# <a name="options-text-editor-cc-advanced"></a>Opciones, editor de texto, C/C++, avanzado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Al cambiar estas opciones, puede modificar el comportamiento relacionado con IntelliSense y la base de datos de exploración cuando programa en C o C++.  
  
 Para tener acceso a esta página, en el cuadro de diálogo **Opciones**, en el panel izquierdo, expanda **Editor de texto**, expanda **C/C++** y, después, pulse **Opciones avanzadas**.  
  
> [!NOTE]
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Vea [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="browsingnavigation"></a>Exploración o navegación  
 Nunca debería elegir estas opciones excepto en el caso excepcional donde una solución sea tan grande que la actividad de base de datos use una cantidad inaceptable de recursos del sistema.  
  
 **Deshabilitar la base de datos**  
 Todo el uso del código que examina la base de datos (SDF), todas las demás opciones de exploración o navegación, y todas las características de IntelliSense salvo Autocompletar #include se deshabilitan.  
  
 **Deshabilitar las actualizaciones de la base de datos**  
 La base de datos se abrirá en modo de solo lectura y no se realizarán actualizaciones a medida que se editen los archivos. La mayoría de las características seguirán funcionando. En cambio, cuando se realicen las modificaciones, los datos quedarán obsoletos y obtendrá resultados incorrectos.  
  
 **Deshabilitar las actualizaciones automáticas de la base de datos**  
 La base de datos de exploración de código no se actualizará automáticamente cuando se modifiquen los archivos de código fuente. En cambio, si abre el **Explorador de soluciones**, abre el menú contextual del proyecto y, después, pulsa **Volver a examinar la solución**, todos los archivos obsoletos se comprobarán y la base de datos se actualizará.  
  
 **Deshabilitar los archivos implícitos**  
 La base de datos de exploración de código no recopila datos para los archivos que no se especifican en un proyecto. Un proyecto contiene archivos de origen y archivos de encabezado que se especifican explícitamente. Los archivos implícitos se incluyen mediante archivos explícitos (por ejemplo, afxwin.h, windows.h y atlbase.h). Normalmente, el sistema busca estos archivos y también los indexa para diferentes características de exploración (incluida Navegar a). Si elige esta opción, esos archivos no se indexan y algunas características no están disponibles para ellos. Si elige esta opción, "Deshabilitar limpieza implícita" y "Deshabilitar carpetas de dependencias externas" también se eligen de manera implícita.  
  
 **Deshabilitar limpieza implícita**  
 La base de datos de exploración de código no limpia archivos implícitos a los que ya no se hace referencia. Esta opción impide que los archivos implícitos se quiten de la base de datos cuando ya no se usan. Por ejemplo, si agrega una directiva `#include` que hace referencia a mapi.h en uno de los archivos de origen, mapi.h se encontrará e indexará. Si después quita #include y no se hace referencia al archivo en ningún lugar, la información sobre este se quitará finalmente a menos que elija esta opción. (Vea la opción **Intervalo para volver a examinar la solución**). Esta opción se ignora cuando vuelve a examinar la solución explícitamente.  
  
 **Deshabilitar las carpetas de dependencias externas**  
 La carpeta Dependencias externas de cada proyecto no se crea ni se actualiza. En el **Explorador de soluciones**, cada proyecto contiene una carpeta de dependencias externas, que contiene todos los archivos implícitos de ese proyecto. Si elige esta opción, esa carpeta no aparece.  
  
 **Volver a crear la base de datos**  
 Vuelva a crear la base de datos de exploración de código desde cero la próxima vez que se cargue la solución. Si elige esta opción, el archivo de base de datos SDF se elimina la próxima vez que cargue la solución, por lo que la base de datos se volverá a crear y todos los archivos se indexarán.  
  
 **Intervalo para volver a examinar la solución**  
 Un trabajo "Volver a examinar la solución ahora" está programado para el intervalo que especifique. Debe especificar un valor entre 0 y 5000 minutos. El valor predeterminado es de 60 minutos. Mientras la solución se vuelve a examinar, las marcas de tiempo de archivo se comprueban para determinar si un archivo se ha cambiado fuera del IDE. (Los cambios que se realizan en el IDE se detectan automáticamente y los archivos se actualizan). Los archivos incluidos implícitamente se comprueban para determinar si todavía se hace referencia a todos ellos.  
  
## <a name="diagnostic-logging"></a>Registro de diagnóstico  
 Estas opciones se proporcionan en caso de que Microsoft le pida recopilar información avanzada para diagnosticar un problema. La información de registro no es útil para los usuarios y recomendamos que la mantenga deshabilitada.  
  
 **Habilitar el registro**  
 Habilita el registro de diagnóstico en la ventana de salida.  
  
 **Nivel de registro**  
 Establezca el nivel de detalle del registro, de 0 a 5.  
  
 **Filtro de registro**  
 Los filtros mostraban tipos de eventos mediante una máscara de bits.  
  
 Puede establecerlo con una suma de alguna de las siguientes opciones:  
  
-   0 - Ninguno  
  
-   1 - General  
  
-   2 - Inactivo  
  
-   4 - WorkItem  
  
-   8 - IntelliSense  
  
-   16 - ACPerf  
  
-   32 - ClassView  
  
## <a name="fallback-location"></a>Ubicación de recursos de reserva  
 La ubicación de recursos de reserva es el lugar donde se colocan los archivos auxiliares de SDF e IntelliSense (por ejemplo, iPCH) cuando la ubicación principal (mismo directorio que la solución) no se usa. Esta situación puede producirse si el usuario no tiene permisos para escribir en el directorio de la solución o este se encuentra en un dispositivo lento. La ubicación de recursos de reserva predeterminada está en el directorio temporal del usuario.  
  
 **Usar siempre ubicación de recursos de reserva**  
 Indica que los archivos de la base de datos de exploración de código y de IntelliSense deben almacenarse siempre en una carpeta que especifique como la "Ubicación de recursos de reserva", no junto al archivo .sln. El IDE nunca intentará colocar los archivos SDF o iPCH junto al directorio de la solución y siempre usará la ubicación de recursos de reserva.  
  
 **No advertir si se usa una ubicación de recursos de reserva**  
 No se le informará ni preguntará si se usa una "Ubicación de recursos de reserva". Normalmente, el IDE le indicará si tuvo que usar la ubicación de recursos de reserva. Esta opción desactiva esa advertencia.  
  
 **Ubicación de recursos de reserva**  
 Este valor se usa como una ubicación secundaria para almacenar la base de datos de exploración de código o los archivos IntelliSense. De manera predeterminada, el directorio temporal es su ubicación de recursos de reserva. El IDE creará un subdirectorio en la ruta especificada (o el directorio temporal) que incluye el nombre de la solución junto con un hash de la ruta de acceso completa a la solución, lo que evita problemas con nombres de solución que son idénticos.  
  
## <a name="intellisense"></a>IntelliSense  
 **Información rápida automática**  
 Permite información rápida cuando mueve el puntero sobre el texto.  
  
 **Deshabilitar IntelliSense**  
 Deshabilita todas las características de IntelliSense. El IDE no crea procesos VCPkgSrv.exe para atender las solicitudes de IntelliSense, y ninguna característica de IntelliSense funcionará (Información rápida, Lista de miembros, Autocompletar, Ayuda de Parám). La coloración semántica y el resaltado de referencias también están deshabilitados. Esta opción no deshabilita las características de exploración que se basan únicamente en la base de datos (incluida la barra de navegación, ClassView y la ventana Propiedades).  
  
 **Deshabilitar actualización automática**  
 La actualización de IntelliSense se retrasa hasta que se realice una solicitud real de IntelliSense. Este retraso puede provocar un tiempo de ejecución mayor de la primera operación de IntelliSense en un archivo, pero puede resultar útil para establecer esta opción en equipos con recursos limitados o muy lentos. Si elige esta opción, también elige implícitamente las opciones "Deshabilitar informe de errores" y "Deshabilitar subrayados ondulados".  
  
 **Deshabilitar informe de errores**  
 Deshabilita los informes de errores de IntelliSense con subrayados ondulados y la ventana Lista de errores. También deshabilita el análisis en segundo plano asociado con los informes de errores. Si elige esta opción, también elige implícitamente la opción "Deshabilitar subrayados ondulados".  
  
 **Deshabilitar subrayados ondulados**  
 Deshabilita los subrayados ondulados de errores de IntelliSense. Los "subrayados ondulados" rojos no se muestran en la ventana del editor, pero el error seguirá apareciendo en la ventana Lista de errores.  
  
 **Deshabilitar autocompletado #include**  
 Deshabilita el autocompletado de instrucciones `#include`.  
  
 **Usar barra diagonal en autocompletado #include**  
 Desencadena el autocompletado de instrucciones `#include` cuando se usa "/". El delimitador predeterminado es la barra diagonal inversa "\". El compilador puede aceptar cualquiera, por lo que use esta opción para especificar la que usa su código base.  
  
 **Unidades máximas de traducción en caché**  
 Número máximo de unidades de traducción que se mantendrán activas al mismo tiempo para solicitudes de IntelliSense. Debe especificar un valor entre 2 y 15. Este número se relaciona directamente con el número máximo de procesos VCPkgSrv.exe que se ejecutarán (para una instancia determinada de Visual Studio). El valor predeterminado es 2, pero si tiene memoria disponible, puede aumentar este valor y posiblemente conseguir un rendimiento ligeramente mejor en IntelliSense.  
  
 Para obtener más información sobre unidades de traducción, vea [Fases de traducción](http://msdn.microsoft.com/library/a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db).  
  
 **Deshabilitar lista de miembros absoluta**  
 La lista de miembros no aparece mientras escribe el nombre de un tipo o una variable. La lista aparece solo después de que escriba uno de los caracteres de confirmación, según lo definido en la opción **Caracteres de confirmación de las listas de miembros**.  
  
 **Deshabilitar palabras clave de listas de miembros**  
 Las palabras clave de lenguaje como `void`, `class`, `switch` no aparecen en las sugerencias de lista de miembros.  
  
 **Deshabilitar fragmentos de código de listas de miembros**  
 Los fragmentos de código no aparecen en las sugerencias de lista de miembros.  
  
 **Deshabilitar coloración semántica**  
 Desactiva toda la coloración de código excepto para las palabras clave de lenguaje, cadenas y comentarios.  
  
 **Confirmación automática de las listas de miembros**  
 Agrega una línea cuando pulsa la tecla Entrar al final de una palabra completa.  
  
 **Modo de filtro de la lista de miembros**  
 Establece el tipo de algoritmo de coincidencia. **Aproximada** busca las coincidencias más posibles porque usa un algoritmo que es similar a un corrector ortográfico para buscar coincidencias que sean similares pero no idénticas. **Filtrado inteligente** coincide con subcadenas incluso si no se encuentran al comienzo de una palabra. **Prefijo** solo coincide con subcadenas idénticas que comienzan al principio de la palabra.  
  
 **Caracteres de confirmación de las listas de miembros**  
 Especifica los caracteres que provocan que se confirme la sugerencia de lista de miembros resaltada en ese momento. Puede agregar o quitar caracteres de esta lista.  
  
## <a name="references"></a>Referencias  
 **Deshabilitar resolución**  
 Por razones de rendimiento, "Buscar todas las referencias" mostrará los resultados de la búsqueda de texto sin formato de manera predeterminada, en lugar de usar IntelliSense para comprobar cada candidato. Puede desactivar esta casilla para obtener resultados más precisos en todas las operaciones de búsqueda. Para filtrar en una base por búsqueda, abra el menú contextual para obtener la lista de resultados y, después, pulse "Resolver resultados".  
  
 **Ocultar no confirmados**  
 Ocultar elementos no confirmados en los resultados de "Buscar todas las referencias". Si no establece la opción "Deshabilitar resolución", puede usar esta opción para ocultar los elementos no confirmados en los resultados.  
  
 **Deshabilitar resaltado de referencia**  
  
## <a name="see-also"></a>Vea también  
 [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)



