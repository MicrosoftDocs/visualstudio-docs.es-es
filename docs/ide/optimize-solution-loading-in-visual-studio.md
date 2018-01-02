---
redirect_url: /visualstudio/ide/optimize-visual-studio-startup-time/
ms.openlocfilehash: 6ba351d5b395caaddd12021b09f8792cd19b2905
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2017
---
title: "Optimización de la carga de soluciones en Visual Studio | Microsoft Docs" ms.custom: "" ms.date: 08/31/2017 ms.reviewer: "" ms.suite: "" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "startup time [Visual Studio]"
  - "optimizing startup time [Visual Studio]"
  - "speed up start time [Visual Studio]" ms.assetid: 84989983-84bc-4f81-97a8-2131e3a25138 caps.latest.revision: 4 author: "gewarren" ms.author: "gewarren" manager: ghogen f1_keywords: 
  - "vs.performancecenter" ms.technology: 
  - "vs-ide-general"
---
# <a name="optimize-solution-loading-in-visual-studio"></a>Optimización de la carga de soluciones en Visual Studio
Muchas soluciones contienen un gran número de proyectos, lo que afecta al tiempo necesario para cargarlas. Pero en entornos de equipo, los programadores suelen trabajar con un subconjunto diferente de proyectos y no necesitan cargar todos los proyectos individuales.

Visual Studio 2017 es compatible con la **carga de solución ligera**. Cuando se habilita el modo de carga de solución ligera (LSL), Visual Studio 2017 carga un pequeño subconjunto de proyectos en lugar de cargar todos los proyectos de una solución de gran tamaño. La mayoría de las características del IDE usadas con frecuencia funcionan en el modo LSL, lo que permite compilar, buscar y depurar en toda la solución. (La principal característica que no se admite en el modo LSL es Editar y continuar).  

> [!NOTE]
> Este contenido se aplica a Visual Studio 2017 Update 3.

En el caso de las soluciones de gran tamaño con más de 30 proyectos, LSL suele cargar las soluciones el doble de rápido (de media). Mientras que la mayoría de las características del IDE funcionan en el modo LSL, algunas pueden requerir que se carguen todos los proyectos. En estos casos, Visual Studio carga automáticamente toda la solución para que pueda usar la característica. En el peor de los casos, acabará cargando todos los proyectos en el modo ligero. 

Si usa una característica del IDE en un proyecto que no está cargado, Visual Studio carga el proyecto adecuado. Por ejemplo, si está intentando crear o abrir un diagrama de clases para un proyecto que no está abierto, Visual Studio carga automáticamente los proyectos adecuados. En las secciones siguientes se indica una lista detallada de características.

En las secciones siguientes se muestra cómo habilitar la carga de solución ligera y se incluye información que le ayudará a decidir si quiere habilitar la característica.

## <a name="enable-or-disable-lightweight-solution-load"></a>Habilitación o deshabilitación de la característica Carga de solución ligera

Puede hacer clic con el botón derecho en el nombre de la solución en el Explorador de soluciones y seleccionar **Habilitar la carga de solución ligera**. Después de seleccionar la opción, debe cerrar y volver a abrir la solución para activar la carga de la solución ligera.

> [!NOTE]
> Para deshabilitar LSL, los pasos son similares. Si quiere deshabilitar la carga de solución ligera, seleccione **Deshabilitar la carga de solución ligera** y, después, cierre y vuelva a abrir la solución. 

![Explorador de soluciones](../ide/media/VSIDE_LSL_Solution_Setting.png)

## <a name="global_solution_load_settings"></a>Definir la configuración global para la carga de solución ligera

Puede deshabilitar o configurar LSL de manera global para todas las soluciones. Para ello, elija **Herramientas > Opciones > Proyectos y soluciones**.

![Cuadro de diálogo Opciones de herramientas](../ide/media/VSIDE_LightweightSolutionLoad.png)

## <a name="how-does-lightweight-solution-load-work-behind-the-scenes"></a>¿Cómo funciona en segundo plano la carga de solución ligera?

Cuando se carga la solución, Visual Studio recuerda qué proyectos ha abierto anteriormente y solo carga dichos proyectos. Todos los demás están visibles en el Explorador de soluciones, pero no se cargan. Cuando haga clic con el botón derecho en un proyecto o lo expanda, Visual Studio lo cargará automáticamente. La carga automática de proyectos suele tardar menos de un segundo, pero en el caso de algunos proyectos puede tardar más. Con todo, Visual Studio habilita características del IDE como búsqueda, depuración, compilación y control de código fuente que funcionan en toda la solución. Por ejemplo, puede buscar en una solución completa aunque solo se hayan cargado unos pocos proyectos en el modo ligero. 

A medida que expanda más proyectos, Visual Studio recordará la lista de proyectos expandidos. Cuando se vuelva a abrir una solución, Visual Studio cargará automáticamente los proyectos previamente expandidos.

## <a name="visual-studio-prompts-developers-likely-to-see-significant-performance-gains"></a>Visual Studio muestra avisos a los desarrolladores que puedan experimentar más mejoras de rendimiento

Según la telemetría de Visual Studio, las soluciones de gran tamaño con más de 30 proyectos se benefician considerablemente del modo LSL. Por lo tanto, se muestra un aviso a los desarrolladores con soluciones de gran tamaño para que prueben el modo LSL. La mayoría de los desarrolladores que prueban LSL por primera vez acaban usándolo de forma habitual. 

## <a name="visual-studio-makes-recommendations-to-turn-on-lightweight-solution-load-based-on-heuristics"></a>Visual Studio hace recomendaciones para activar la carga de solución ligera en función de la heurística

De forma predeterminada, Visual Studio activa LSL para los usuarios con más probabilidades de beneficiarse de su uso. Si tiene varias soluciones, Visual Studio ofrece el modo LSL para las soluciones que probablemente obtendrán más mejoras de rendimiento. Si selecciona la opción del modo ligero **Let Visual Studio decide** (Dejar que decida Visual Studio) (opción predeterminada), Visual Studio podría abrir la solución en el modo ligero en función de la heurística. Una barra de mensajes indica si la solución se encuentra en el modo ligero. Cuando se muestra la barra de mensajes, puede obtener más información o actualizar la configuración.

![Ventana emergente](../ide/media/VSIDE_LSL_Popup.png)

## <a name="ide-features-fully-supported-in-lightweight-mode"></a>Características del IDE totalmente compatibles con el modo ligero

|Característica|¿Compatible con el modo ligero?|
|-|-|-|
|IntelliSense|Sí|
|Buscar|Sí|
|Depuración|Sí|
|Compilar|Sí|
|Navegación de código (Ir a definición y Buscar todas las referencias)|Sí|
|Code Lens|Sí|
|Análisis de código estático|Sí|
|Implementar y publicar|Sí|
|Agregar y quitar referencias|Sí|
|Compatibilidad con múltiples versiones|Sí|
|IntelliTrace|Sí|
|Live Unit Testing|Sí|
|IntelliTest|Sí|
|Microsoft Fakes|Sí|
|Editar y continuar|No compatibles|
|Pruebas unitarias|Requiere la carga de proyectos de prueba seguida de una compilación de soluciones|

## <a name="scenarios-in-which-lightweight-solution-loads-the-appropriate-projects-to-complete-the-operation"></a>Escenarios en los que la solución ligera carga los proyectos adecuados para completar la operación

Si no está trabajando en un proyecto de la solución, el proyecto no se carga en el modo ligero. En el caso de algunas características, los proyectos adicionales se cargan automáticamente para admitir el escenario de característica. (Intentaremos reducir esta lista de escenarios ). Para estos escenarios, Visual Studio cargará automáticamente los proyectos o bien le pedirá que los cargue según sea necesario.

|Categoría|Problema|
|-|-|-|
|Prueba unitaria|Los proyectos que no están cargados actualmente no aparecen en la lista de proyectos de prueba de los asistentes "Crear IntelliTest" y "Crear proyecto de prueba unitaria". </br>Tiene que cargar los proyectos para los que quiere crear pruebas (puede expandir el nodo del proyecto para cargarlo).|
|Diagramas de clases|Si crea o abre un diagrama de clases de un proyecto, Visual Studio carga automáticamente los proyectos que son dependencias directas de ese proyecto. </br>Si no se carga la solución completa, se desactiva la validación de artefactos obsoletos a los que hace referencia un diagrama de validación de dependencias.|

## <a name="scenarios-in-which-lightweight-solution-loads-the-entire-solution"></a>Escenarios en los que la solución ligera carga toda la solución 

Para algunas características, Visual Studio carga automáticamente toda la solución para admitir el escenario. Esta acción garantiza que siempre obtendrá la funcionalidad completa. Por ejemplo, algunas operaciones de TFS pueden requerir que se cargue toda la solución. Para proporcionar una funcionalidad completa, Visual Studio carga toda la solución.

|Categoría|Escenario|
|-|-|-|
|Comando SCC de TFS en el nodo de la solución|Si se desencadena un comando SCC en el nodo de la solución (en el Explorador de soluciones), Visual Studio carga automáticamente toda la solución antes de completar el comando.|
|Carga del proyecto|Si la solución contiene proyectos de .NET Core y compartidos, Visual Studio siempre carga automáticamente estos proyectos durante la carga inicial de la solución. Estos proyectos no admiten actualmente el modo ligero.|
|Administrador de configuración de soluciones|Si usa el administrador de configuración de soluciones o la compilación por lotes, Visual Studio carga automáticamente toda la solución para ofrecer una experiencia completa.|
|Administrador de paquetes de NuGet|Si abre la interfaz de usuario del administrador de paquetes de NuGet o la consola del administrador de paquetes de NuGet, Visual Studio carga automáticamente toda la solución para proporcionar una experiencia completa.|

## <a name="known-issues"></a>Problemas conocidos

Algunos escenarios podrían no funcionar en el modo LSL y requieren la carga de proyectos adicionales o de toda la solución. Estamos trabajando activamente para resolver estos casos. 

|Categoría|Problema|Solución|
|-|-|-|-|
|IntelliSense|Puede que IntelliSense no se actualice tras un cambio de configuración (por ejemplo, al cambiar de compilación de versión a depuración y viceversa). El impacto dependerá de las diferencias de código surgidas a raíz del cambio de configuración.|Vuelva a cargar la solución después de cambiar la configuración.|
|Limitaciones de refactorización para proyectos de C#/VB|Las correcciones de código que cambian los archivos de proyecto pueden producir un error en modo silencioso la primera vez.|Cargue los proyectos si necesita realizar correcciones de código en archivos de estos proyectos. El modo ligero no realiza correcciones en los proyectos que no se han cargado.|
|Detección de pruebas unitarias|Las pruebas detectadas en proyectos diferidos no se ejecutan cuando un proyecto se carga manualmente.|Recompile el proyecto para volver a detectar las pruebas y ejecute de nuevo las pruebas seleccionadas.|
|Live Unit Testing (LUT)|En el modo LSL, puede ver que LUT no está activado. Esto se debe a que LUT necesita que se cargue uno de los proyectos de prueba.|Cargue cualquier proyecto de prueba para activar Live Unit Testing para la solución.|
|Búsqueda en el Explorador de soluciones|1.    La búsqueda del Explorador de soluciones en el modo LSL no busca en los archivos y no devuelve resultados de progresión (es decir, solo se muestran archivos en el árbol de búsqueda, pero no clases, métodos, etc.).</br>2.    Todos los archivos que pertenecen a un proyecto se muestran como una lista plana, en lugar de una vista de árbol. Cuando los archivos pertenecen a una carpeta de un proyecto, se muestra la ruta de acceso relativa del archivo, en lugar de simplemente el nombre de archivo en la vista de búsqueda.</br>No hay ningún menú contextual relativo a los elementos de archivo en la vista de búsqueda.|Cargue la solución completa en un modo que no sea LSL para usar la búsqueda tradicional del Explorador de soluciones.</br>También puede usar la búsqueda del IDE de Visual Studio.|
|Examinador de objetos para proyectos de C++|El Examinador de objetos muestra las referencias de ensamblado/WinMD únicamente para los proyectos cargados.|Cargue los proyectos cuya información quiera ver en el Examinador de objetos.|

> [!Note]
> Gracias a nuestros partners, las extensiones populares, incluida ReSharper, también funcionan correctamente con la carga de solución ligera.

Estamos muy contentos con las innovaciones para optimizar el rendimiento del tiempo de carga de soluciones para los desarrolladores. Dado que se trata de una característica nueva, nos estamos volcando en analizar los comentarios de los clientes y resolver los problemas conocidos. Esperamos recibir sus comentarios. Puede enviar un correo electrónico al equipo de optimización de la carga de soluciones de Visual Studio a la dirección lslsupport@microsoft.com

## <a name="see-also"></a>Vea también
[Sugerencias y trucos de rendimiento de Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)  