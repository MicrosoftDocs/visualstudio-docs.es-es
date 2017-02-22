---
title: "Glosario de Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Glosario [Visual Studio SDK]"
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Glosario de Visual Studio SDK
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este glosario proporciona definiciones de términos que se usan en el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentación.  
  
## Términos  
 complemento  
 Una aplicación de utilidad, controlador u otro software que se agregan a una aplicación primaria. En el entorno de desarrollo integrado \(IDE\) de Visual Studio, un complemento es una aplicación basada en la automatización que amplía las capacidades del IDE.  
  
 modelo de automatización  
 El modelo de automatización, conocido en versiones anteriores de Visual Studio como el modelo de extensibilidad, es una interfaz de programación que le proporciona acceso a las rutinas subyacentes que controlan el IDE. Complementos, asistentes y macros utilizan objetos en el modelo de automatización para controlar o amplían la funcionalidad del IDE.  
  
 contexto de la interfaz de usuario de comandos  
 Asociación de un GUID con la visibilidad de un elemento, como una barra de herramientas o un comando de interfaz de usuario. Contexto de la interfaz de usuario de comandos es como el contexto de selección de no está conectado a una ventana.  
  
 Contexto de la interfaz de usuario de comandos puede utilizarse para:  
  
-   Asignar un GUID a una barra de herramientas que aparece cuando se activa una ventana concreta.  
  
-   Asignar un GUID a la disponibilidad de un comando sin tener que cargar o ejecutar un paquete VSPackage.  
  
-   Asignar un GUID para afectan al enlace de teclado activa.  
  
-   Asignar un GUID para activar la grabación de macros.  
  
-   Asignar un GUID para activar el modo de depuración o para alternar entre el diseño y el modo de ejecución en un editor.  
  
 component  
 Componente de software que se puede realizar parte de la funcionalidad de la aplicación sin esa aplicación tener toda la información acerca de la implementación del software existente. La comunicación entre un componente y una aplicación es únicamente a través de interfaces de estilo OLE.  
  
 Administrador de componentes  
 Un servicio, `SOleComponentManager`, que proporciona servicios de coordinación de interfaz de usuario no para los componentes de nivel superior. El `SOleComponentManager` servicio implementa la `IOleComponentManager` interfaz.  
  
 Administrador de componentes de interfaz de usuario  
 Un servicio, `SOleComponentUIManager`, que proporciona servicios de coordinación de interfaz de usuario. El `SOleComponentUIManager` servicio implementa la `IOleComponentUIManager` y `IOleInPlaceComponentUIManager` interfaces.  
  
 conjunto de contextos  
 Un `IVsUserContext` objeto \(COM\) asociado a un componente de entorno. Este objeto contiene palabras clave de búsqueda, palabras clave F1 y atributos relacionados con el componente. Bolsas de contexto además apuntar a cualquier bolsas subcontexto que están vinculados a ellos.  
  
 proveedor de contexto  
 Un componente en el IDE, que tiene un contenedor de contexto asociado con él. Estos componentes incluyen una ventana de herramientas, el editor o la jerarquía del proyecto.  
  
 designer  
 Interfaz de programación que permite a los usuarios manipular los elementos de la interfaz de usuario \(formularios, botones y otros controles\).  
  
 DocData  
 Un objeto COM que encapsula los datos subyacentes de un documento en un mundo donde hay separación documento\/vista \(por ejemplo, en el caso del editor de texto, esto sería el búfer de texto subyacente todas las vistas del editor de texto\). Si el EditorFactory no proporciona este objeto, el IDE fabricará uno en su lugar. La responsabilidad de este objeto es administrar la persistencia de los datos y la semántica de uso compartido para varias vistas sobre este mismo `DocData`. Si el `DocData` objeto admite el `IOleCommandTarget` interfaz, se incluirá en el enrutamiento de comandos de la UIShell.  
  
 DocObject  
 Tecnología utilizada para hospedar la interfaz de usuario dentro de un marco proporcionado por el host. Más concretamente, este término hace referencia a la inserción que admite la `IOleDocument` y las interfaces relacionadas. Esta tecnología tiene muchas aplicaciones posibles como un detalle de implementación de documentos de COM, las ventanas de herramientas en Visual Basic 5.0, los diseñadores de ActiveX en Visual Basic 6.0 y así sucesivamente.  
  
 documento  
 Utilizado para hacer referencia genéricamente al documento como un todo, tanto los `DocData` y `DocView`. Por ejemplo, contiene un DocumentFrame un `DocView`, pero también mantiene una referencia a la `DocData` para controlar la persistencia.  
  
 DocView  
 El DocObject\/Embedding o panel de la ventana con el que el usuario interactúa para ver y manipular subyacente `DocData`. Tenga en cuenta que los usuarios aprovecha las ventajas de la separación de documentos y vistas que forma parte de la `DocObject` Diseño de la interfaz. Los usuarios utilizar un DocObject todo para actuar como una vista en lugar de usar una noción más abstractos \(y menos formal\) de datos subyacentes que se conoce como `DocData`.`DocView` los objetos siempre se incrustan con objetos de marco de documento \(ventanas secundarias de MDI\) del IDE.  
  
 DTE  
 La `DTE` objeto \(extensibilidad de herramientas de desarrollo\) es el punto de acceso de nivel superior en el modelo de automatización de Visual Studio, lo que permite automatizar y extender el IDE mediante programación.  
  
 Ventana de Ayuda dinámica  
 Ventana de herramientas que se implementa mediante el IDE y muestra una lista de palabras clave de búsqueda o temas de Ayuda de F1.  
  
 Editor de  
 Código \(clase, CLSID\) que implementa el `DocView`. También implementa `DocData` Si se admite la separación de datos o vista.  
  
 extensión  
 Una característica que modifica, personaliza o se agrega a un IDE. Crear extensiones mediante el modelo de automatización o VSPackages.  
  
 editor externo  
 Un editor que no es específico del IDE, como Microsoft Word. Se ha registrado a través de sus propios mecanismos y se puede usar fuera del IDE. Si se puede incrustar este editor, aparece dentro de una ventana en el IDE. Si no se puede incrustar, se crea una ventana de nivel superior.  
  
 jerarquía  
 Árbol de nodos, cada nodo asociado a un conjunto de propiedades.  
  
 componente de nivel superior independiente  
 Un componente que utiliza una ventana de nivel superior no modal y puede funcionar eficazmente como una ventana de aplicación independiente, pero se implementa como un objeto en proceso. Por lo tanto, un componente de nivel superior independiente debe coordinar modalidad y servicios de bucle de mensajes con el IDE. Objetos de proceso no tienen su propio bucle de mensajes.  
  
 proveedor de información  
 El proveedor de información es un módulo que se puede buscar palabras clave y devolver una lista de temas, en forma de `IVsUserContextItem` objetos. Para proporcionar elementos de palabra clave F1 y búsqueda para el proveedor de información, registre el archivo de Ayuda compilado \(. HxS\) con el sistema. Los temas de Ayuda de estos archivos se utilizan para proporcionar la lista de temas que se muestran en la ventana Ayuda dinámica y se muestra si un usuario presiona F1.  
  
 componente en contexto  
 Un objeto VSPackage que implemente el `IOleInPlaceComponent` interfaz para administrar una ventana que visualmente está dentro de una ventana de documento posee el IDE. Componentes en contexto no participan en estándar: combinación de menús; en su lugar se integran los elementos de la interfaz de usuario en el IDE.  
  
 Hay dos tipos de componentes en contexto: cableado in situ componentes y controles del componente.  
  
 Componentes de hardware en el lugar tienen menús, barras de herramientas y comandos que se integran estrechamente en la interfaz de usuario del IDE, que aparecen como si se compilaron directamente en el IDE.  
  
 Controles de componente no tiene ninguno de sus propios elementos de interfaz de usuario integrados en el IDE; en su lugar utilizan menús, comandos y barras de herramientas del IDE. Por ejemplo, el comando Bold podría usarse en negrita a una palabra seleccionada dentro de un control de texto enriquecido incrustado en un formulario. Sin embargo, los controles de componente pueden solicitar que se mostrarán elementos de interfaz de usuario específicos del componente instalados de forma dinámica.  
  
 servicio de lenguaje  
 Un conjunto de objetos que permite a los desarrolladores de VSPackage implementar características de editores de código de lenguaje de equipo, como texto marcado y el coloreado.  
  
 Proyecto de archivos varios  
 Proyecto que se utiliza para alojar archivos abiertos que no están en cualquier proyecto. No se conserva la lista de elementos de este proyecto.  
  
 proyecto  
 Los proyectos se componen de objetos de la jerarquía u objetos COM que implementan la `IVsHierarchy` interfaz.  
  
 Diseñador específica del proyecto o el editor  
 Diseñador no se pueden utilizar independientemente del tipo de proyecto. Todos los diseñadores específicos del proyecto deben introducir su información de generador del Editor del registro. El IDE, a continuación, puede crear una instancia del diseñador siempre que se abre un determinado tipo de archivo en un proyecto concreto.  
  
 ventana de tipo de proyecto  
 Una ventana que constantemente realiza el seguimiento de la jerarquía del proyecto activo actualmente y el elemento desde el contexto de selección global. Tipo de proyecto windows utiliza el `SVsTrackSelectionEx` servicio para el IDE de cambios de alerta y mostrar comentarios para el usuario. El Explorador de soluciones es un ejemplo de una ventana de tipo de proyecto.  
  
 Propiedades \(ventana\)  
 Examinador de propiedades anteriormente.  
  
 proyectos de referencia  
 Proyecto que no requieren los archivos del proyecto en el mismo directorio. En su lugar, las referencias a archivos de otros directorios no relacionados se almacenan y mantenidas por el propio proyecto.  
  
 tabla de documentos de ejecución  
 Estructura interna que el IDE mantiene la lista de todos los documentos abiertos actualmente. Esta lista incluye todos los documentos abiertos en memoria independientemente de si los documentos se esté editando. Un documento es cualquier elemento que se guarda, incluidos los procedimientos almacenados que se abre en un editor, archivos de un proyecto o el archivo de proyecto principal \(por ejemplo, un archivo \*.vcproj\).  
  
 contexto de selección  
 Datos que forma parte de los detalles de cada ventana en el IDE y se utilizan para realizar un seguimiento de las selecciones activas. Contexto de selección consta de:  
  
-   Puntero a la `IVsHierarchy` la interfaz de la jerarquía del proyecto  
  
-   Identificador de elemento del elemento de proyecto.  
  
-   Puntero a la `ISelectionContainer` interfaz que proporciona acceso a propiedades de los objetos activos.  
  
-   Matriz de valores de elemento.  
  
 servicio  
 Un contrato para un conjunto de interfaces COM que residen en un único objeto COM. Cuando se crea un servicio, que se identifica mediante un GUID, se define el conjunto de interfaces COM que lleva a cabo el servicio. Objetos COM usan servicios para comunicarse entre sí.  
  
 solución  
 Grupo de proyectos relacionados con la que un usuario trabaja.  
  
 Diseñador estándar  
 Un diseñador puede usarse independientemente del tipo de proyecto. Todos los diseñadores estándares deben introducir su información de generador del Editor del registro. El IDE, a continuación, puede crear una instancia del diseñador siempre que se abre un archivo con una extensión específica. Deben guardar los datos en un archivo.  
  
 editor estándar  
 Editor que se puede utilizar de forma independiente de cualquier tipo de proyecto determinado. Estos editores tienen EditorFactories registrado en el registro. Esto permite que el IDE buscar y llamar al editor.  
  
 editor estándar de sistema operativo  
 Una incrustación no es Visual Studio específico. Se ha registrado con las claves conocidas de Win32 \(por ejemplo, el Explorador de Win32 sabe cómo invocar\). Si se puede incrustar un editor de este tipo, el editor aún aparecerá en su lugar en el IDE. De lo contrario, se crea una ventana de nivel superior para dichos editores.  
  
 contenedor de subcontexto  
 Un `IVsUserContext` objeto vinculado a un contenedor de contextos. Este objeto contiene los atributos de una selección dentro de un componente IDE, palabras clave F1 y palabras clave de consulta. Subcontexto ejemplos de un comando en una ventana de herramientas o una palabra clave en un editor.  
  
 Lista de tareas  
 Ventana de herramientas que se implementa mediante el IDE y muestra una lista de tareas activas.  
  
 búfer de texto  
 Nombre común del objeto `VSTextBuffer`.  
  
 Vista de texto  
 Nombre común del objeto `VSTextView`.  
  
 componente de nivel superior de la herramienta  
 Un componente que funciona como una ventana emergente no modal, coordinación estrechamente con la interfaz de usuario del IDE. Como los componentes de nivel superior independientes, los componentes de nivel superior de la herramienta también deben coordinar modalidad y servicios de bucle de mensajes con el IDE.  
  
 componente de nivel superior  
 Un objeto VSPackage que administra una ventana no modal de nivel superior en lugar del área de cliente de una ventana del IDE. Implementan componentes de nivel superior la `IOleComponent` interfaz para aprovechar los servicios de bucle de mensajes, como el acceso al tiempo de inactividad.  
  
 Interfaz de usuario activo  
 Un objeto VSPackage visible y que tiene actualmente el foco.  
  
 Jerarquía de la interfaz de usuario  
 Un objeto COM que implementa el `IVsUIHierarchy` interfaz para permitir la visualización de una jerarquía. La ventana de jerarquía de la interfaz de usuario se implementa la `ISelectionContainer` de la interfaz para actualizar la ventana Propiedades; otras ventanas de tipo de proyecto pueden utilizar esta implementación, si lo desea.  
  
 VSCT  
 Tabla de comandos de Visual Studio. El archivo .vsct contiene información sobre la ubicación y los comportamientos de menús, barras de herramientas y comandos en formato XML.  
  
 VSPackage  
 Un componente instalable de software que amplía el IDE de Visual Studio que contribuyen a una o varias de las siguientes acciones: interfaz de usuario, servicios, tipos de proyecto o editor o diseñador. Un VSPackage consta de un objeto COM que implementa el `IVsPackage` interfaz y uno o varios otros objetos COM que implementan otras interfaces para admitir la selección y otras características. Además, un paquete VSPackage tiene requisitos de registro específico.