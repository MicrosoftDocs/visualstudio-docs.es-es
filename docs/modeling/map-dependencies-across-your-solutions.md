---
title: Asignar dependencias en sus soluciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
ms.assetid: e04850a2-17c5-459b-93ec-6c74143b3292
caps.latest.revision: "243"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: fc8d9774c69216136eb2b4c99b379ef1c714997f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="map-dependencies-across-your-solutions"></a>Asignar dependencias de sus soluciones
Si desea comprender las dependencias de todo su código, cree mapas de código para visualizarlas. Esto ayuda a ver cómo encaja el código sin necesidad de leer archivos y líneas de código.  
  
 ![Ver las dependencias de sus soluciones](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
 **A continuación encontrará unos vídeos**:  
  
-   [Comprenda las dependencias del código visualizándolas](http://go.microsoft.com/fwlink/?LinkID=252065)  
  
-   [Visualice el impacto de un cambio](http://go.microsoft.com/fwlink/?LinkID=252068)  
  
-   [Comprensión del código complejo con ayuda del mapa de código](http://go.microsoft.com/fwlink/?LinkID=259869)  
  
##  <a name="GetStarted"></a> Introducción a los mapas de código  
 **Para poder usar mapas de código necesitará una**:  
  
-   Visual Studio Enterprise: permite crear mapas de código desde el editor de código, el explorador de soluciones, la vista de clases o el examinador de objetos.  
  
-   Visual Studio Professional: permite abrir mapas de código, realizar ediciones limitadas y navegar por código.  
  
> [!WARNING]
>  Antes de compartir los mapas creados en Visual Studio Enterprise con otros usuarios que usen Visual Studio Professional, asegúrese de que todos los elementos del mapa son visibles (por ejemplo, los elementos ocultos, los grupos expandidos y los vínculos entre grupos).  
  
 **Las dependencias de código se pueden asignar en los siguientes lenguajes**:  
  
-   Visual C# .NET o Visual Basic .NET en una solución o ensamblados (.dll o .exe)  
  
-   Código de C o C++ nativo o administrado en proyectos de Visual C++, archivos de encabezado (.h o `#include`) o archivos binarios  
  
-   Proyectos y ensamblados de X++ creados desde módulos de .NET para Microsoft Dynamics AX  
  
 **Nota:** para los proyectos que no sean de C# o Visual Basic. NET, no hay tantas opciones para iniciar un mapa de código o agregar elementos a un mapa de código existente. Por ejemplo, no podrá hacer clic con el botón secundario en un objeto en el editor de texto de un proyecto de C++ y agregarlo a un mapa de código. Sin embargo, puede arrastrar y colocar elementos de código individuales o archivos desde el Explorador de soluciones, la Vista de clases y el Examinador de objetos.  
  
#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>Para ver las dependencias generales de la solución  
  
1.  Abra el menú **Arquitectura** .  
  
2.  Si acaba de abrir la solución y aún no la ha compilado, o si el código ha cambiado desde la última vez que se compiló, elija **Generar mapa de código para solución**.  
  
3.  Si el código no ha cambiado desde la última vez que se compiló, elija **Generar mapa de código para una solución sin compilación** para que la creación del mapa sea más rápida.  
  
4.  [Vea las dependencias generales](#SeeOverviewSource) para comprender cómo puede usar mapas de código para ver las dependencias globales en toda la solución.  
  
#### <a name="to-see-specific-dependencies-within-your-solution"></a>Para ver dependencias concretas de la solución  
  
1.  Con la solución cargada, abra el **Explorador de soluciones**.  
  
2.  Seleccione los proyectos, las referencias de ensamblado, las carpetas, los archivos, los tipos o los miembros que desee asignar.  
  
3.  En el **el Explorador de soluciones** barra de herramientas, elija **mostrar en mapa de código**![crear nuevo gráfico de nodos botón seleccionados](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton "). O bien, abra el menú contextual y elija **Mostrar en mapa de código**. También puede arrastrar elementos desde la vista de clases o el examinador de objetos en un mapa de código nuevo o existente.  
  
4.  [Vea las dependencias específicas](#SeeSpecificSource) para comprender cómo puede usar mapas de código para ver dependencias específicas de su solución.  
  
###  <a name="CreateEmptyMap"></a> Para agregar un nuevo mapa de código vacío a la solución  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del nodo de la solución de nivel superior. Elija **Agregar** y **Nuevo elemento**.  
  
2.  Bajo **Instalado**, elija **General**.  
  
3.  En el panel derecho, elija **Documento de gráfico dirigido** y después elija **Agregar**.  
  
     Ahora tiene un mapa en blanco que aparece en la carpeta **Elementos de la solución** de su solución.  
  
#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>Para crear un nuevo mapa de código vacío sin agregarlo a la solución  
  
1.  Abra el menú **Arquitectura** y elija **Nuevo mapa de código**.  
  
     \- o -  
  
2.  Abra el menú **Archivo** y elija **Nuevo** y luego elija **Archivo**.  
  
3.  Bajo **Instalado**, elija **General**.  
  
4.  En el panel derecho, elija **Documento de gráfico dirigido** y después elija **Abrir**.  
  
     Ahora tiene un mapa en blanco que no aparece en las carpetas de su solución.  
  
##  <a name="SeeOverviewSource"></a> Vea las dependencias generales  
  
###  <a name="OverviewSource"></a> Ver las dependencias de su solución  
  
1.  En el menú **Arquitectura** , elija **Generar mapa de código para solución**.  
  
     ![Generar un comando de mapa de código](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")  
  
     Obtendrá un mapa que muestra los ensamblados de nivel superior y los vínculos agregados entre ellos. Cuanto más amplio sea el vínculo agregado, más dependencias representará.  
  
2.  Use el botón **Leyenda** situado en la barra de herramientas del mapa de código para mostrar u ocultar la lista de iconos de tipo de proyecto (por ejemplo, proyectos de prueba, web y teléfono), los elementos de código (por ejemplo, clases, métodos y propiedades) y los tipos de relación (por ejemplo, “Se hereda de”, “Implementa” y “Llama a”).  
  
     ![Top &#45; gráfico de dependencias de nivel de ensamblados](../modeling/media/dependencygraph_toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")  
  
     Esta solución de ejemplo contiene carpetas de solución (**Pruebas** y **Componentes**), proyectos de prueba, proyectos web y ensamblados. De forma predeterminada, todas las relaciones de contención aparecen como *grupos*que se pueden expandir y contraer. El grupo **Externos** contiene cualquier elemento que esté fuera de la solución, incluidas las dependencias de plataforma. En los ensamblados externos solo se muestran los elementos que están en uso. De forma predeterminada, los tipos base del sistema están ocultos en el mapa para reducir la acumulación de elementos.  
  
3.  Para profundizar en el mapa, expanda los grupos que representan proyectos y ensamblados. Puede expandir todo si presiona **CTRL+A** para seleccionar todos los nodos y, después, elige **Grupo**, **Expandir** en el menú contextual.  
  
     ![Expandiendo todos los grupos en un mapa de código](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")  
  
4.  No obstante, puede que esto no resulte útil en el caso de soluciones grandes. De hecho, con soluciones complejas, las limitaciones de memoria pueden impedirle expandir todos los grupos. En su lugar, expanda un nodo individual para explorarlo. Mueva el puntero del mouse sobre el nodo y luego haga clic en el botón de contenido adicional (flecha hacia abajo) cuando aparezca.  
  
     ![Expandir un nodo en un mapa de código](../modeling/media/dependencygraph_containment.png "DependencyGraph_Containment")  
  
     También puede usar el teclado: seleccione el elemento y luego presione la tecla más (**+**). Para explorar niveles de código más profundos, haga lo mismo para los espacios de nombres, los tipos y los miembros.  
  
    > [!TIP]
    >  Para obtener más información sobre cómo trabajar con código asigna mediante el mouse, teclado y táctil, vea [examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).  
  
5.  Para simplificar el mapa y centrarse en partes individuales, elija **Filtros** en la barra de herramientas del mapa de código y seleccione únicamente los tipos de nodos y los vínculos que le interesan. Por ejemplo, puede ocultar todos los contenedores de la carpeta de soluciones y los ensamblados.  
  
     ![Simplificar el mapa mediante el filtrado de contenedores](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")  
  
     Otra manera de simplificar el mapa es ocultar o quitar grupos y elementos individuales, sin que ello afecte al código subyacente de la solución.  
  
6.  Para ver las relaciones entre los elementos, selecciónelos en el mapa. Los colores de los vínculos indican los tipos de relación, tal como se muestra en el panel **Leyenda** .  
  
     ![Ver las dependencias de sus soluciones](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
     En este ejemplo, los vínculos de color púrpura son llamadas, los vínculos con puntos son referencias y los vínculos de color azul claro son acceso a campos. Los vínculos verdes pueden ser herencia o pueden ser *vínculos agregados* que indican más de un tipo de relación (o *categoría*).  
  
    > [!TIP]
    >  Si ve un vínculo verde, podría no significar únicamente que hay una relación de herencia. También puede haber llamadas de método, ocultas por la relación de herencia. Para ver determinados tipos de vínculos, use las casillas de verificación en la **filtros** panel para ocultar los tipos no le interesan.  
  
7.  Para más información sobre un elemento o vínculo, mueva el puntero por encima hasta que aparezca información. De este modo se mostrarán los detalles de un elemento de código o las categorías que representa un vínculo.  
  
     ![Mostrar las categorías de una relación](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")  
  
8.  Para examinar los elementos y las dependencias representados por un vínculo agregado, primero seleccione el vínculo y luego abra su menú contextual. Elija **Mostrar vínculos de contribución** (o **Mostrar vínculos de contribución en el nuevo mapa de código**). De este modo se expanden los grupos en ambos extremos del vínculo y se muestran solo los elementos y dependencias que participan en el vínculo.  
  
9. Para centrarse en partes específicas del mapa, puede continuar quitar elementos que no le interesa. Por ejemplo, para ver los detalles en la vista de clases y miembros, simplemente filtre todos los nodos de espacios de nombres en el panel **Filtros** .  
  
     ![Profundizando hasta el nivel de clase y miembro](../modeling/media/dependencygraph_expandedselectedgroups_2012.png "DependencyGraph_ExpandedSelectedGroups_2012")  
  
10. Otra manera de centrarse en un mapa de solución compleja consiste en generar un mapa nuevo que contenga los elementos seleccionados en un mapa existente. Mantenga presionada la tecla **CTRL** mientras selecciona los elementos en los que desea centrarse, abra el menú contextual y elija **Nuevo gráfico a partir de selección**.  
  
     ![Mostrar los elementos seleccionados en un nuevo mapa de código](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")  
  
11. El contexto contenedor se traslada al nuevo mapa. Ocultar carpetas de soluciones y cualquier otro contenedor que no desee ver mediante el **filtros** panel.  
  
     ![Filtrar los contenedores para simplificar la vista](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")  
  
12. Expanda los grupos y seleccione elementos en el mapa para ver las relaciones.  
  
     ![Seleccionar elementos para ver las relaciones](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")  
  
 Vea también:  
  
-   [Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)  
  
-   Busque posibles problemas en el código mediante la [ejecución de un analizador](../modeling/find-potential-problems-using-code-map-analyzers.md).  
  
###  <a name="OverviewCompiled"></a> Ver las dependencias entre ensamblados o archivos binarios  
  
1.  [Cree un mapa de código vacío](#GetStarted)o abra un mapa de código existente (archivo .dgml).  
  
2.  Arrastre hasta el mapa los ensamblados o los archivos binarios que desee asignar desde fuera de Visual Studio. Por ejemplo, arrastre los ensamblados o los archivos binarios desde el Explorador de Windows o el Explorador de archivos.  
  
> [!NOTE]
>  Solo puede arrastrar ensamblados o archivos binarios desde el Explorador de Windows o el Explorador de archivos si ejecuta tanto dichos exploradores como Visual Studio en el mismo nivel de permisos del Control de cuentas de usuario (UAC). Por ejemplo, si UAC está activado y está ejecutando Visual Studio como administrador, el Explorador de Windows o el Explorador de archivos bloquearán la operación de arrastre. Para resolver este problema, asegúrese de que ambos se ejecutan con el mismo nivel de permisos o desactive UAC.  
  
##  <a name="SeeSpecificSource"></a> Vea las dependencias específicas  
 Por ejemplo, suponga que debe realizar una revisión de código en unos archivos con cambios pendientes. Para ver las dependencias que hay en esos cambios, cree un mapa de código a partir de dichos archivos.  
  
 ![Mostrar las dependencias específicas en un mapa de código](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
### <a name="see-specific-dependencies-in-your-solution"></a>Ver dependencias concretas de la solución  
  
1.  Abra el **Explorador de soluciones**. Seleccione los proyectos, las referencias de ensamblado, las carpetas, los archivos, los tipos y los miembros que le interesen. Para buscar elementos que dependen de tipos o miembros, abra el menú contextual del tipo o del miembro desde el **Explorador de soluciones**. Elija el tipo de dependencia y, después, seleccione los resultados.  
  
2.  Asigne los elementos y sus miembros. En el **el Explorador de soluciones** barra de herramientas haga clic en **mostrar en mapa de código**![crear nuevo gráfico de nodos botón seleccionados](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").  
  
     ![Seleccione los elementos que desea asignar](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")  
  
3.  El mapa muestra los elementos seleccionados dentro de los ensamblados que los contienen.  
  
     ![Los elementos se muestran como grupos en el mapa seleccionados](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")  
  
     También puede arrastrar elementos desde el explorador de soluciones, la vista de clases o el examinador de objetos a un mapa de código existente o en blanco. Para crear un mapa en blanco, vea el artículo sobre cómo [crear un mapa de código vacío](#GetStarted). Para incluir la jerarquía primaria para sus elementos, mantenga presionada la tecla **CTRL** mientras arrastra los elementos, o bien use el botón **Incluir elementos primarios** en la barra de herramientas del mapa de código para especificar la acción predeterminada.  
  
    > [!NOTE]
    >  Cuando se agregan elementos de un proyecto que se comparte entre varias aplicaciones, como Windows Phone o la Tienda Windows, dichos elementos aparecen en el mapa con el proyecto de aplicación activo actualmente. Si cambia el contexto a otro proyecto de aplicación y agrega más elementos del proyecto compartido, dichos elementos aparecerán ahora con el nuevo proyecto de aplicación activo. Las operaciones que se realizan con un elemento en el mapa solo se aplican a los elementos que comparten el mismo contexto.  
  
4.  Para explorar los elementos, expándalos. Mueva el puntero del mouse sobre un elemento y luego haga clic en el botón de contenido adicional (flecha hacia abajo) cuando aparezca.  
  
     ![Expandir un nodo en un mapa de código](../modeling/media/dependencygraph_containment.png "DependencyGraph_Containment")  
  
     Para expandir todos los elementos, selecciónelos mediante **CTRL+A**y luego abra el menú contextual del mapa y elija **Grupo**, **Expandir**. Sin embargo, esta opción no está disponible si el hecho de expandir todos los grupos genera un mapa que no se puede usar o problemas de memoria.  
  
5.  Continúe expandiendo los elementos que le interesen hasta el nivel de clase y miembro (si es necesario).  
  
     ![Expandir los grupos al nivel de clase y miembro](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")  
  
     Para ver los miembros que están en el código pero no aparecen en el mapa, haga clic en el **volver a obtener elementos secundarios** icono ![volver a obtener elementos secundarios icono](../modeling/media/dependencygraph_deletednodesicon.png "DependencyGraph_DeletedNodesIcon") en la parte superior esquina izquierda de un grupo.  
  
6.  Para ver más elementos relacionados con los del mapa, seleccione uno y elija **Mostrar relacionados** en la barra de herramientas del mapa de código, y luego seleccione el tipo de elementos relacionados que se agregarán al mapa. Como alternativa, seleccione uno o más elementos, abra el menú contextual y, a continuación, elija la **mostrar...**  opción para el tipo de elementos relacionados para agregar al mapa. Por ejemplo:  
  
     Para un **ensamblado**, elija:  
  
    |||  
    |-|-|  
    |**Mostrar ensamblados a los que este hace referencia**|Agregue los ensamblados a los que este ensamblado hace referencia. Los ensamblados externos aparecen en el grupo **Externos** .|  
    |**Mostrar ensamblados que hacen referencia a este**|Agregue los ensamblados de la solución que hacen referencia a este ensamblado.|  
  
     Para un **espacio de nombres**, elija **Mostrar ensamblado contenedor**, si no está visible.  
  
     Para una **clase** o **interfaz**, elija:  
  
    |||  
    |-|-|  
    |**Mostrar tipos base**|Para una clase, agregue la clase base, así como las interfaces implementadas.<br /><br /> Para una interfaz, agregue las interfaces base.|  
    |**Mostrar tipos derivados**|Para una clase, agregue las clases derivadas.<br /><br /> Para una interfaz, agregue las interfaces derivadas y las clases o structs de implementación.|  
    |**Mostrar tipos a los que este hace referencia**|Agregue todas las clases y los miembros que esta clase utilice.|  
    |**Mostrar tipos que hacen referencia a este**|Agregue todas las clases y los miembros que usan esta clase.|  
    |**Mostrar espacio de nombres contenedor**|Agregue el espacio de nombres primario.|  
    |**Mostrar espacio de nombres y ensamblado contenedores**|Agregue la jerarquía de contenedores principales.|  
    |**Mostrar todos los tipos base**|Agregue la jerarquía de interfaz o de clase base de forma recursiva.|  
    |**Mostrar todos los tipos derivados**|Para una clase, agregue todas las clases derivadas de forma recursiva.<br /><br /> Para una interfaz, agregue todas las interfaces derivadas y clases o structs de implementación de forma recursiva.|  
  
     Para un **método**, elija:  
  
    |||  
    |-|-|  
    |**Mostrar métodos a los que este llama**|Agregue los métodos a los que llama este método.|  
    |**Mostrar campos a los que este hace referencia**|Agregue los campos a los que hace referencia este método.|  
    |**Mostrar tipo contenedor**|Agregue el tipo primario.|  
    |**Mostrar tipo, espacio de nombres y ensamblado contenedores**|Agregue la jerarquía de contenedores principales.|  
    |**Mostrar métodos invalidados**|Para obtener un método que invalide otros métodos o que implemente un método de una interfaz, agregue todo el resumen o los métodos virtuales en las clases base invalidadas y, si existe, el método de interfaz implementado.|  
  
     Para un **campo** o **propiedad**, elija:  
  
    |||  
    |-|-|  
    |**Mostrar tipo contenedor**|Agregue el tipo primario.|  
    |**Mostrar tipo, espacio de nombres y ensamblado contenedores**|Agregue la jerarquía de contenedores principales.|  
  
     ![Mostrar métodos llamados por este miembro](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")  
  
7.  El mapa muestra las relaciones. En este ejemplo, se muestran los métodos llamados por el método `Find` y su ubicación en la solución o externa.  
  
     ![Mostrar las dependencias específicas en un mapa de código](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
8.  Para simplificar el mapa y centrarse en partes individuales, elija **Filtros** en la barra de herramientas del mapa de código y seleccione únicamente los tipos de nodos y los vínculos que le interesan. Por ejemplo, desactive la visualización de carpetas de soluciones, ensamblados y espacios de nombres.  
  
     ![Utilice el panel de filtro para simplificar la presentación](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")  
  
##  <a name="SeeSourceHeader"></a> Ver las dependencias entre los archivos de código fuente de C y C++ y los archivos de encabezado  
 Si desea crear mapas más completos para proyectos de C++, establezca en dichos proyectos la opción del compilador de información de examen (**/FR**). Si no, aparece un mensaje que le solicita establecer esta opción. Si selecciona **Aceptar**, la opción se establece solamente en el mapa actual. Si lo desea, puede ocultar el mensaje para todos los mapas posteriores. Si oculta este mensaje, puede hacer que aparezca de nuevo. Establezca la siguiente clave del registro en `0` o elimine la clave:  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\NativeProvider: AutoEnableSbr**  
  
 Al abrir una solución que contiene proyectos de Visual C++, podría llevar algún tiempo la actualización de la base de datos de IntelliSense. Durante este tiempo, quizás no pueda crear mapas de código para los archivos de encabezado (.h o `#include`) hasta que la base de datos de IntelliSense finalice la actualización. Puede supervisar el progreso de actualización en la barra de estado de Visual Studio. Para resolver los problemas o los mensajes que aparecen porque ciertas opciones de IntelliSense están deshabilitadas, vea el artículo sobre [solución de problemas de mapas de código C y C++](#Troubleshooting).  
  
-   Para ver las dependencias entre todos los archivos de código fuente y los archivos de encabezado de la solución, vaya al menú **Arquitectura** y elija **Generar gráfico de archivos de inclusión**.  
  
     ![Gráfico de dependencias para código nativo](../modeling/media/dependencygraphgeneral_nativecode.png "DependencyGraphGeneral_NativeCode")  
  
-   Para ver las dependencias entre el archivo abierto actualmente y los archivos de código fuente y de encabezado relacionados, abra el archivo de origen o el archivo de encabezado. Abra el menú contextual del archivo desde cualquier parte del archivo. Elija **Generar gráficos de archivos de inclusión**.  
  
     ![Primer &#45; gráfico de dependencias de nivel para archivo .h](../modeling/media/dependencygraph_native_firstlevel.png "DependencyGraph_Native_FirstLevel")  
  
###  <a name="Troubleshooting"></a> solución de problemas de mapas de código C y C++  
 Estos elementos no se admiten para código de C y C++:  
  
-   Los tipos base no aparecen en los mapas que incluyen la jerarquía primaria.  
  
-   La mayoría de los elementos de menú **Mostrar** no están disponibles para el código de C y C++.  
  
 Los siguientes problemas podrían producirse al crear mapas de código para código de C y C++:  
  
|**Problema**|**Causa posible**|**Resolución**|  
|---------------|------------------------|--------------------|  
|El mapa de código no se generó.|No se compiló correctamente ningún proyecto de la solución.|Corrija los errores de compilación que se produjeron y, después, vuelva a generar el mapa.|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no responde al intentar generar un mapa de código desde el menú **Arquitectura** .|El archivo de base de datos de programa (.pdb) podría estar dañado.<br /><br /> Un archivo .pdb almacena la información de depuración, como tipo, método e información del archivo de código fuente.|Recompile la solución y, a continuación, inténtelo de nuevo.|  
|Cierta configuración de la base de datos de navegador de IntelliSense está deshabilitada.|Cierta configuración de IntelliSense podría estar deshabilitada en el cuadro de diálogo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**de** .|Active los valores para habilitarla.<br /><br /> Vea [opciones, Editor de texto, C/C ++, avanzado](../ide/reference/options-text-editor-c-cpp-advanced.md).|  
|Aparece el mensaje **Métodos desconocidos** en un nodo de método.<br /><br /> Este problema se produce porque no se puede resolver el nombre del método.|El archivo binario podría no tener una tabla de reubicación base.|Active la opción **/FIXED:NO** en el vinculador.|  
||El archivo de base de datos de programa (.pdb) podría no estar compilado.<br /><br /> Un archivo .pdb almacena la información de depuración, como tipo, método e información del archivo de código fuente.|Active la opción **/DEBUG** en el vinculador.|  
||No se puede abrir o encontrar el archivo .pdb en las ubicaciones esperadas.|Asegúrese de que existe el archivo .pdb en las ubicaciones esperadas.|  
||Se ha quitado la información de depuración del archivo .pdb.|Si se ha usado la opción **/PDBSTRIPPED** en el vinculador, incluya el archivo .pdb completo en su lugar.|  
||El llamador no es una función y, o bien es un código thunk en el archivo binario o es un puntero en la sección de datos.|Cuando el llamador es un código thunk, intente usar `_declspec(dllimport)` para evitar el código thunk.|  
  
##  <a name="RenderMoreQuickly"></a> Acelerar la representación de los mapas de código  
 Al generar por primera vez un mapa, Visual Studio indiza todas las dependencias que encuentra. Este proceso puede tardar algún tiempo, especialmente con soluciones de gran tamaño, pero mejorará el rendimiento posterior. Si el código cambia, Visual Studio solo vuelve a indizar el código actualizado. Para minimizar el tiempo necesario para que el mapa la asignación de finalizar la representación, considere las siguientes opciones:  
  
-   [Asigne solo las dependencias que le interesan.](#SeeSpecificSource)  
  
-   Antes de generar el mapa de toda una solución, reduzca el ámbito de dicha solución.  
  
-   Desactive la compilación automática de la solución con el botón **Omitir compilación** de la barra de herramientas del mapa de código.  
  
-   Desactive la inclusión automática de elementos primarios con el botón **Incluir elementos primarios** de la barra de herramientas del mapa de código.  
  
-   Edite directamente el mapa de código para quitar los nodos y los vínculos que no necesite. Cambiar el mapa no afecta al código subyacente. Vea [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
 ![Los botones SKIP Build e incluir elementos primarios](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")  
  
 Aunque Visual Studio puede ejecutarse con 1 GB de memoria, le recomendamos que el equipo tenga al menos 2 GB de memoria para evitar demoras mientras Visual Studio crea el índice de código y genera el mapa.  
  
 Podría llevar más tiempo crear mapas o agregar elementos a un mapa desde el Explorador de soluciones si la propiedad **Copiar en el directorio de salida** de un elemento del proyecto se establece en **Copiar siempre**. Esto podría causar problemas en compilaciones incrementales y Visual Studio con cada recompilación del proyecto. Para mejorar el rendimiento, cambie esta propiedad a **Copiar si es posterior** o `PreserveNewest`. Vea [Incremental Builds](../msbuild/incremental-builds.md).  
  
 El mapa completo mostrará las dependencias únicamente del código compilado correctamente. Si se producen errores de compilación de determinados componentes, dichos errores se mostrarán en mapa. Asegúrese de que un componente se compila realmente y de que tiene dependencias antes de tomar decisiones sobre la arquitectura en función del mapa.  
  
##  <a name="SavingExporting"></a> Compartir mapas de código  
  
### <a name="share-the-map-with-other-visual-studio-users"></a>Compartir el mapa con otros usuarios de Visual Studio  
 Guarde el mapa desde el menú **Archivo** .  
  
 O bien  
  
 Para guardar el mapa como parte de un proyecto específico, en la barra de herramientas del mapa elija **Compartir**, **Mover** \<*CodeMapName*>**.dgml en**y, después, elija el proyecto donde desea guardar el mapa.  
  
 ![Mover un mapa a otro proyecto](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")  
  
 Visual Studio guarda el mapa como un archivo .dgml que se puede compartir con otros usuarios de Visual Studio Enterprise y Visual Studio Professional.  
  
> [!NOTE]
>  Antes de compartir un mapa con usuarios de Visual Studio Professional, asegúrese de expandir los grupos, de mostrar los nodos ocultos y los vínculos entre grupos, y de recuperar los nodos eliminados que desea que los demás vean en el mapa. De lo contrario, los otros usuarios no podrán ver estos elementos.  
>   
>  El error siguiente podría producirse al guardar un mapa que está en un proyecto de modelado o que se copió desde un proyecto de modelado en otra ubicación:  
>   
>  "No se puede guardar *nombreDeArchivo* fuera del directorio del proyecto. No se admiten elementos vinculados".  
>   
>  Visual Studio muestra el error pero crea la versión guardada de todas maneras. Para evitar el error, cree el mapa fuera del proyecto de modelado. Después puede guardarlo en la ubicación que desee. Copiar el archivo en otra ubicación de la solución e intentar guardarlo después no dará resultado.  
  
### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Exportar el mapa como una imagen para que se pueda copiar en otras aplicaciones como Microsoft Word o PowerPoint  
  
1.  En la barra de herramientas del mapa de código, elija **Compartir**, **Correo electrónico como imagen** o **Copiar imagen**.  
  
2.  Pegue la imagen en otra aplicación.  
  
### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Exportar el gráfico como archivo XPS para visualizarlo en visores XML o XAML como Internet Explorer  
  
1.  En la barra de herramientas del mapa de código, elija **Compartir**, **Correo electrónico como XPS portable** o **Guardar como XPS portable**.  
  
2.  Vaya adonde desea guardar el archivo.  
  
3.  Póngale un nombre al mapa de código. Asegúrese de que el **Guardar como tipo** cuadro se establece en **archivos XPS (\*.xps)**. Elija **Guardar**.  
  
## <a name="what-else-can-i-do"></a>¿Qué más puedo hacer?  
  
-   [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)  
  
-   [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
-   [Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
