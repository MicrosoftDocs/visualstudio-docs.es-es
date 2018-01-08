---
title: Glosario de SDK de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa0f7eaed09df717eb0746076715f9c780464df1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-sdk-glossary"></a>Glosario de SDK de Visual Studio
Este glosario proporciona definiciones de términos que se usan en el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentación.  
  
## <a name="terms"></a>Términos  
 complemento  
 Una aplicación de la utilidad, controlador u otro software que se agregan a una aplicación principal. En el entorno de desarrollo integrado (IDE) de Visual Studio, un complemento es una aplicación basada en la automatización que amplía las capacidades del IDE.  
  
 modelo de automatización  
 El modelo de automatización, conocido en versiones anteriores de Visual Studio como el modelo de extensibilidad, es una interfaz de programación que proporciona acceso a las rutinas subyacentes que controlan el IDE. Complementos, asistentes y macros utilizan los objetos en el modelo de automatización para controlar o extienden la funcionalidad del IDE.  
  
 contexto de la interfaz de usuario de comandos  
 Asociación de un GUID con la visibilidad de un elemento, como una barra de herramientas o un comando de interfaz de usuario. Contexto de la interfaz de usuario de comandos es a diferencia de contexto de la selección ya que no está conectado a una ventana.  
  
 Contexto de la interfaz de usuario de comandos puede utilizarse para:  
  
-   Asignar un GUID a una barra de herramientas que aparece cuando se activa una ventana concreta.  
  
-   Asignar un GUID a la disponibilidad de un comando sin tener que cargar o ejecutar un paquete VSPackage.  
  
-   Asignar un GUID para que afecten al enlace de teclado activa.  
  
-   Asignar un GUID para activar la grabación de macros.  
  
-   Asignar un GUID para activar el modo de depuración o para alternar entre el diseño y modo de ejecución en un editor.  
  
 component  
 Componente de software que puede formar parte de funcionalidad de la aplicación sin esa aplicación que tiene toda la información acerca de la implementación del software existente. La comunicación entre un componente y una aplicación es únicamente a través de interfaces de estilo OLE.  
  
 Administrador de componentes  
 Un servicio, `SOleComponentManager`, que proporciona servicios de coordinación de interfaz de usuario no para los componentes de nivel superior. El `SOleComponentManager` servicio implementa el `IOleComponentManager` interfaz.  
  
 Administrador de componentes de interfaz de usuario  
 Un servicio, `SOleComponentUIManager`, que proporciona servicios de coordinación de interfaz de usuario. El `SOleComponentUIManager` servicio implementa el `IOleComponentUIManager` y `IOleInPlaceComponentUIManager` interfaces.  
  
 conjunto de contextos  
 Un `IVsUserContext` objeto (COM) que se adjunta a un componente de entorno. Este objeto contiene palabras clave de búsqueda, palabras clave de F1 y atributos que se relacionan con el componente. Bolsas de contexto además apuntar a cualquier bolsas subcontexto que están vinculados a ellos.  
  
 proveedor de contexto  
 Un componente en el IDE que tiene un conjunto de contextos asociado a él. Estos componentes incluyen una ventana de herramientas, el editor o la jerarquía de proyecto.  
  
 designer  
 Una interfaz de programación que permite a los usuarios manipular los elementos de la interfaz de usuario (formularios, botones y otros controles).  
  
 DocData  
 Un objeto COM encapsula los datos subyacentes de un documento en un mundo donde hay separación documento/vista (por ejemplo, en el caso de editor de texto, esto sería el búfer de texto subyacente todas las vistas del editor de texto). Si el EditorFactory no proporciona este objeto, el IDE fabrica uno en su nombre. Es la responsabilidad de este objeto administrar la persistencia de los datos y la semántica de uso compartido para varias vistas sobre este mismo `DocData`. Si el `DocData` objeto admite el `IOleCommandTarget` interfaz, se incluirá en el enrutamiento de comandos de la UIShell.  
  
 DocObject  
 Tecnología que se usa para hospedar la interfaz de usuario en un intervalo proporcionado por el host. Más concretamente, este término hace referencia a la inserción que admite el `IOleDocument` y relacionados con interfaces. Esta tecnología tiene muchas posibles aplicaciones tales como un detalle de implementación de documentos de COM, las ventanas de herramientas en Visual Basic 5.0, los diseñadores de ActiveX en Visual Basic 6.0 y así sucesivamente.  
  
 documento  
 Utilizado para hacer referencia genéricamente al documento en su totalidad, tanto el `DocData` y `DocView`. Por ejemplo, contiene un DocumentFrame un `DocView`, pero también mantiene una referencia a la `DocData` para controlar la persistencia.  
  
 DocView  
 El DocObject/Embedding/panel de la ventana con el que el usuario interactúa para ver y manipular subyacente `DocData`. Tenga en cuenta que los usuarios no aprovechar las ventajas de la separación de documento/vista que forma parte de la `DocObject` diseño de la interfaz. Los usuarios utilizar un DocObject completo para que actúe como una vista en lugar de usar una noción más abstracto (y menos formalizado) de datos subyacentes que se conoce como `DocData`. `DocView`objetos siempre se incrustan con objetos de marco de documento (ventanas secundarias MDI) del IDE.  
  
 DTE  
 La `DTE` objeto (extensibilidad de herramientas de desarrollo) es el punto de acceso de nivel superior en el modelo de automatización de Visual Studio, lo que permite automatizar y extender el IDE mediante programación.  
  
 Ventana de Ayuda dinámica  
 Ventana de herramientas que se implementa mediante el IDE y muestra una lista de palabras clave de búsqueda o temas de Ayuda de F1.  
  
 editor  
 Código (clase, CLSID) que implementa el `DocView`. También implementa `DocData` si se admite la separación de datos o de la vista.  
  
 extensión  
 Una característica que modifica, personaliza, o agrega un IDE. Crear extensiones mediante el modelo de automatización o VSPackages.  
  
 editor externo  
 Un editor que no es específico para el IDE, como Microsoft Word. Se ha registrado a través de sus propios mecanismos y puede utilizarse fuera del IDE. Si este editor se puede incrustar, aparece dentro de una ventana en el IDE. Si no se puede incrustar, se crea una ventana de nivel superior independiente.  
  
 jerarquía  
 Árbol de nodos, cada nodo asociado a un conjunto de propiedades.  
  
 componente de nivel superior independiente  
 Un componente que utiliza una ventana de nivel superior no modal y puede funcionar eficazmente como una ventana de aplicación independiente, pero se implementa como un objeto en proceso. Por lo tanto, un componente de nivel superior independiente debe coordinar modalidad y servicios de bucle de mensajes con el IDE. Objetos de proceso no tienen su propio bucle de mensajes.  
  
 proveedor de información  
 El proveedor de información es un módulo que se puede buscar palabras clave y devolver una lista de temas, en forma de `IVsUserContextItem` objetos. Para proporcionar elementos de palabra clave de F1 y búsqueda para el proveedor de información, registre el archivo de Ayuda compilado (. HxS) con el sistema. Los temas de Ayuda de estos archivos se utilizan para proporcionar la lista de temas que se muestran en la ventana Ayuda dinámica y se muestra si un usuario presiona la tecla F1.  
  
 componente en contexto  
 Un objeto de VSPackage que implemente el `IOleInPlaceComponent` interfaz para administrar una ventana que visualmente está dentro de una ventana de documento que posee el IDE. Componentes vigentes no participan en estándar OLE: combinación de menús; en su lugar, los elementos de la interfaz de usuario que se integran en el IDE.  
  
 Hay dos tipos de componentes de in situ: hardware in situ componentes y controles de componente.  
  
 Componentes de hardware en lugar tengan menús, barras de herramientas y comandos que se integran estrechamente en la interfaz de usuario del IDE, que aparecen como si se compilaron directamente en el IDE.  
  
 Controles de componente no tiene ninguno de sus propios elementos de la interfaz de usuario integrados en el IDE; en su lugar utilizan menús, comandos y barras de herramientas del IDE. Por ejemplo, el comando Bold podría utilizarse para una palabra seleccionada dentro de un control de texto enriquecido incrustado en un formulario en negrita. Sin embargo, los controles de componente pueden solicitar que se mostrarán elementos de interfaz de usuario específicos del componente instalados de forma dinámica.  
  
 Servicio de lenguaje  
 Un conjunto de objetos que permite a los desarrolladores de VSPackage implementar características de editores de código de idioma de equipo, como texto marcar y colorear.  
  
 Proyecto de archivos varios  
 Proyecto que se utilizan para alojar archivos abiertos que no están en ningún proyecto. No se conserva la lista de elementos de este proyecto.  
  
 proyecto  
 Los proyectos se componen de objetos hierarchy u objetos COM que implementan la `IVsHierarchy` interfaz.  
  
 específica del proyecto diseñador o editor  
 Un diseñador que no se puede utilizar independientemente del tipo de proyecto. Todos los diseñadores de específica del proyecto deben introducir su información de generador del Editor del registro. El IDE, a continuación, puede crear instancias del diseñador siempre que un determinado tipo de archivo se abre en un proyecto determinado.  
  
 ventana de tipo de proyecto  
 Una ventana que constantemente realiza un seguimiento de la jerarquía del proyecto activo actualmente y el elemento desde el contexto de la selección global. Ventanas de tipo de proyecto la `SVsTrackSelectionEx` servicio para que le alerte al IDE de cambios y para mostrar los comentarios para el usuario. El Explorador de soluciones es un ejemplo de una ventana de tipo de proyecto.  
  
 Propiedades (ventana)  
 Explorador de propiedades anteriormente.  
  
 proyectos basados en la referencia  
 Proyecto que no requieren los archivos del proyecto estar en el mismo directorio. En su lugar, las referencias a archivos de otros directorios no relacionados se almacenan y mantenidas por el propio proyecto.  
  
 tabla de documentos en ejecución  
 Estructura interna de forma que el IDE conserva la lista de todos los documentos abiertos actualmente. Esta lista incluye todos los documentos abiertos en memoria independientemente de si actualmente se está editando los documentos. Un documento es cualquier elemento que se guarda, incluidos los procedimientos almacenados abiertos en un editor, archivos de un proyecto o el archivo de proyecto principal (por ejemplo, un archivo *.vcproj).  
  
 Contexto de selección  
 Datos que forma parte de los detalles de cada ventana en el IDE y se utilizan para realizar un seguimiento de las selecciones activas. Contexto de selección se compone de:  
  
-   Puntero a la `IVsHierarchy` interfaz de la jerarquía del proyecto  
  
-   Identificador del elemento del elemento de proyecto.  
  
-   Puntero a la `ISelectionContainer` interfaz que proporciona acceso a las propiedades de los objetos activos.  
  
-   Matriz de valores de elemento.  
  
 service  
 Un contrato para un conjunto de interfaces COM que residen en un único objeto COM. Cuando se crea un servicio, que se identifica mediante un GUID, definir el conjunto de interfaces COM que lleva a cabo el servicio. Objetos COM usan servicios para comunicarse entre sí.  
  
 Solución  
 Grupo de proyectos relacionados con la que un usuario trabaja.  
  
 Diseñador estándar  
 Un diseñador que se puede usar independientemente del tipo de proyecto. Todos los diseñadores estándares deben introducir su información de generador del Editor del registro. El IDE, a continuación, puede crear instancias del diseñador cuando se abre un archivo con una extensión específica. Deben conservar los datos en un archivo.  
  
 editor estándar  
 Editor que se puede usar independientemente de cualquier tipo de proyecto determinado. Estos editores tienen EditorFactories registrado en el registro. Esto permite que el IDE localizar e invocar el editor.  
  
 editor de sistema operativo estándar  
 Incrustar una que no es Visual Studio específico. Se registra con las claves conocidas de Win32 (por ejemplo, el Explorador de Win32 sabe cómo invocar). Si se puede incrustar un editor de este tipo, el editor aún se mostrará en su lugar en el IDE. En caso contrario, se crea una ventana de nivel superior independiente de tales editores.  
  
 contenedor de subcontexto  
 Un `IVsUserContext` objeto vinculado a un contenedor de contexto. Este objeto contiene palabras clave de búsqueda, palabras clave de F1 y atributos de una selección dentro de un componente IDE. Ejemplos de subcontexto incluyen un comando en una ventana de herramientas o una palabra clave en un editor.  
  
 Lista de tareas  
 Ventana de herramientas que se implementa mediante el IDE y muestra una lista de tareas activas.  
  
 Búfer de texto  
 Nombre común para el objeto `VSTextBuffer`.  
  
 Vista de texto  
 Nombre común para el objeto `VSTextView`.  
  
 componente de nivel superior de la herramienta  
 Un componente que funciona como una ventana emergente no modal, coordinar estrechamente con la interfaz de usuario del IDE. Al igual que los componentes de nivel superior independientes, componentes de nivel superior de la herramienta también deben coordinar modalidad y servicios de bucle de mensajes con el IDE.  
  
 componente de nivel superior  
 Un objeto de VSPackage que administra una ventana no modal de nivel superior en lugar del área de cliente de una ventana del IDE. Implementan componentes de nivel superior la `IOleComponent` interfaz para aprovechar las ventajas de servicios de bucle de mensajes, como el acceso al tiempo de inactividad.  
  
 Interfaz de usuario activa  
 Un objeto de VSPackage que está visible y que tiene actualmente el foco.  
  
 Jerarquía de la interfaz de usuario  
 Un objeto COM que implementa el `IVsUIHierarchy` interfaz para permitir la visualización de una jerarquía. La ventana de la jerarquía de interfaz de usuario se implementa la `ISelectionContainer` de la interfaz para actualizar la ventana Propiedades; otras ventanas de tipo de proyecto pueden utilizar esta implementación, si lo desea.  
  
 VSCT  
 Tabla de comandos de Visual Studio. El archivo .vsct contiene información sobre la selección de ubicación y los comportamientos de menús, barras de herramientas y comandos en formato XML.  
  
 VSPackage  
 Un componente instalable de software que extiende el IDE de Visual Studio al contribuir con una o varias de las siguientes acciones: interfaz de usuario, servicios, tipos de proyecto o editor o diseñador. Un VSPackage consta de un objeto COM que implementa el `IVsPackage` interfaz y uno o varios otros objetos COM que implementan otras interfaces para admitir la selección y otras características. Además, un VSPackage tiene requisitos de registro concreta.