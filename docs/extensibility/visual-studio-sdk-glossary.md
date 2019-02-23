---
title: Glosario de Visual Studio SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6157b4bc3537a4f88feb91d512241451b8324ba7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682809"
---
# <a name="visual-studio-sdk-glossary"></a>Glosario Visual Studio SDK
Este glosario proporciona definiciones de términos que se usan en el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentación.

## <a name="terms"></a>Términos
 complemento de una aplicación de utilidad, controlador u otro software que se agregan a una aplicación principal. En el entorno de desarrollo integrado (IDE) de Visual Studio, un complemento es una aplicación basada en la automatización que amplía las capacidades del IDE.

 modelo de automatización del modelo de automatización, conocido en versiones anteriores de Visual Studio como el modelo de extensibilidad, es una interfaz de programación que le proporciona acceso a las rutinas subyacentes que controlan el IDE. Complementos, asistentes y macros utilizan objetos en el modelo de automatización para controlar o extienden la funcionalidad del IDE.

 Asociación de un GUID con la visibilidad de un comando de la interfaz de usuario o un elemento, como una barra de herramientas del contexto de interfaz de usuario de comandos. Contexto de interfaz de usuario de comandos es a diferencia de contexto de selección que no está adjunta a una ventana.

 Contexto de interfaz de usuario de comandos puede usarse para:

- Asignar un GUID a una barra de herramientas que aparece cuando se activa una ventana concreta.

- Asignar un GUID a la disponibilidad de un comando sin tener que cargar o ejecutar un paquete VSPackage.

- Asignar un GUID que afectan al enlace de teclado activos.

- Asignar un GUID para activar la grabación de macros.

- Asignar un GUID para activar el modo de depuración o para alternar entre el diseño y modo de ejecución en un editor.

  componente de software que se pueden realizar parte de la funcionalidad de una aplicación sin esa aplicación que tiene toda la información sobre la implementación del software previamente existente. La comunicación entre un componente y una aplicación es únicamente a través de interfaces de estilo OLE.

  servicio de administrador de un componente, `SOleComponentManager`, que proporciona servicios de coordinación de interfaz de usuario que no son para los componentes de nivel superior. El `SOleComponentManager` servicio implementa el `IOleComponentManager` interfaz.

  servicio de un administrador de interfaz de usuario de componente, `SOleComponentUIManager`, que proporciona servicios de coordinación de interfaz de usuario. El `SOleComponentUIManager` servicio implementa el `IOleComponentUIManager` y `IOleInPlaceComponentUIManager` interfaces.

  contenedor de contexto un `IVsUserContext` objeto (COM) asociado a un componente de entorno. Este objeto contiene palabras clave de búsqueda, **F1** palabras clave y los atributos que se relacionan con el componente. Además punto bolsas de contexto a los contenedores de subcontexto que están vinculados a ellos.

  componente de un proveedor de contexto en el IDE que tiene un contenedor de contexto asociado con él. Estos componentes incluyen una ventana de herramientas, el editor o la jerarquía del proyecto.

  Diseñador de una interfaz de programación que permite a los usuarios manipular los elementos de la interfaz de usuario (formularios, botones y otros controles).

  Objeto de DocData A COM que encapsula los datos subyacentes de un documento en un mundo donde hay separación de documento/vista (por ejemplo, en el caso del editor de texto, esto sería el búfer de texto subyacente todas las vistas de editor de texto). Si el EditorFactory no suministra este objeto, el IDE fabrica uno en su lugar. La responsabilidad de este objeto es administrar la persistencia de datos y la semántica de uso compartido para varias vistas a través de este mismo `DocData`. Si el `DocData` objeto admite el `IOleCommandTarget` interfaz, ha incluido en el enrutamiento de comandos de la UIShell.

  Tecnología de DocObject se usa para hospedar la interfaz de usuario dentro de un marco proporcionado por el host. Más concretamente, este término hace referencia a la inserción que admita la `IOleDocument` y las interfaces relacionadas. Esta tecnología tiene muchas posibles aplicaciones tales como un detalle de implementación de documentos de COM, ventanas de herramientas en Visual Basic 5.0, los diseñadores de ActiveX en Visual Basic 6.0 y así sucesivamente.

  se usa para hacer referencia genéricamente al documento como un conjunto de documentos, tanto el `DocData` y `DocView`. Por ejemplo, contiene un DocumentFrame un `DocView`, pero también mantiene una referencia a la `DocData` para controlar la persistencia.

  DocView The DocObject/Embedding/panel de la ventana con el que el usuario interactúa para ver y manipular subyacente `DocData`. Los usuarios no aprovechar la separación de la vista del documento que forma parte de la `DocObject` diseño de interfaces. Los usuarios usar un DocObject todo para que actúe como una vista en lugar de usar una noción más abstractos (y menos formal) de datos subyacentes que se conoce como `DocData`. `DocView` los objetos siempre se incrustan con objetos de marco de documento (ventanas secundarias de MDI) del IDE.

  DTE el `DTE` objeto (extensibilidad de herramientas de desarrollo) es el punto de acceso de nivel superior en el modelo de automatización de Visual Studio, lo que permite automatizar y extender el IDE mediante programación.

  Ventana de herramientas de ventana de Ayuda dinámica que se implementa mediante el IDE y muestra una lista de la palabra clave de búsqueda o **F1** temas de ayuda.

  Editor de código (clase, CLSID) que implementa el `DocView`. También implementa `DocData` si se admite la separación de datos y vista.

  característica de una extensión que se modifica, personaliza, o se agrega a un IDE. Crear extensiones mediante el modelo de automatización o VSPackages.

  editor externo un editor que no es específico para el IDE, como Microsoft Word. Se ha registrado a través de sus propios mecanismos y se puede usar fuera del IDE. Si se puede insertar este editor, aparece dentro de una ventana en el IDE. Si no se pueden insertar, se crea una ventana de nivel superior independiente.

  jerarquía de árbol de nodos, cada nodo asociado con un conjunto de propiedades.

  componente de componente de nivel superior independientes A que utiliza una ventana de nivel superior no modal y puede funcionar eficazmente como una ventana de aplicación independiente, pero se implementa como un objeto en proceso. Por lo tanto, un componente independiente de nivel superior debe coordinar modalidad y servicios de bucle de mensajes con el IDE. Los objetos de proceso no tienen su propio bucle de mensajes.

  El proveedor de información de proveedor de información es un módulo que puede buscar palabras clave y devolver una lista de temas, en forma de `IVsUserContextItem` objetos. Para proporcionar **F1** y elementos de la palabra clave de búsqueda para el proveedor de información, registre el archivo de Ayuda compilado (*. HxS*) con el sistema. Los temas de Ayuda de estos archivos proporcionan la lista de temas que se muestran en la ventana Ayuda dinámica y se muestra si un usuario presiona **F1**.

  objeto de un VSPackage del componente que implementa en contexto el `IOleInPlaceComponent` interfaz para administrar una ventana que visualmente es dentro de una ventana de documento que pertenecen a la IDE. Componentes en contexto no participan en estándar OLE-combinación de menús; en su lugar se integran sus elementos de interfaz de usuario en el IDE.

  Hay dos tipos de componentes en contexto: integrado en contexto los componentes y controles de componentes.

  Integrado en contexto componentes tienen menús, barras de herramientas y comandos que se integran estrechamente en la interfaz de usuario del IDE, que aparecen como si se compilaron directamente en el IDE.

  Controles de componentes no tienen ninguno de sus propios elementos de interfaz de usuario integrados en el IDE; en su lugar usan los menús, comandos y las barras de herramientas del IDE. Por ejemplo, podría usar el comando en negrita en negrita una palabra seleccionada dentro de un control de texto enriquecido incrustado en un formulario. Sin embargo, los controles de componentes pueden solicitar que se muestran elementos de interfaz de usuario específicos del componente instalados de forma dinámica.

  lenguaje servicio un conjunto de objetos que permite a los desarrolladores de VSPackage para implementar características de lenguaje informático, como texto marcar y colorear los editores de código.

  Archivos varios del proyecto proyecto usado para los archivos abiertos de enrutamiento que no estén en cualquier proyecto. No se conserva la lista de elementos de este proyecto.

  Proyectos de Project se componen de objetos de la jerarquía o COM, los objetos que implementan la `IVsHierarchy` interfaz.

  específico del proyecto diseñador o editor A diseñador que no se puede usar con independencia del tipo de proyecto. Todos los diseñadores específicos del proyecto deben introducir su información de generador de editores en el registro. El IDE, a continuación, puede crear una instancia del diseñador cada vez que un determinado tipo de archivo se abre en un proyecto concreto.

  ventana de ventana de un tipo de proyecto que constantemente realiza el seguimiento de la jerarquía del proyecto activo actualmente y el elemento desde el contexto de la selección global. Tipo de proyecto windows utiliza el `SVsTrackSelectionEx` servicio alerte al IDE de cambios y para mostrar los comentarios al usuario. El Explorador de soluciones es un ejemplo de una ventana de tipo de proyecto.

  Explorador de propiedades anteriormente en la ventana de propiedades.

  proyectos basados en la referencia de proyecto que no requiere los archivos del proyecto en el mismo directorio. En su lugar, las referencias a archivos de otros directorios no relacionados se almacenan y mantenidas por el propio proyecto.

  estructura interna en la tabla de documento por el que el IDE mantiene la lista de todos los documentos abiertos actualmente en ejecución. La lista incluye todos los documentos abiertos en memoria independientemente de si actualmente se está editando los documentos. Un documento es cualquier elemento que se guarda, incluidos los procedimientos almacenados que se abre en un editor, archivos de un proyecto o el archivo de proyecto principal (por ejemplo, el archivo *.vcproj).

  contexto de selección datos que forma parte de los detalles de cada ventana en el IDE y sirve para realizar un seguimiento de las selecciones activas. Contexto de selección se compone de:

- Puntero a la `IVsHierarchy` interfaz de la jerarquía del proyecto

- Identificador de elemento del elemento de proyecto.

- Puntero a la `ISelectionContainer` interfaz que proporciona acceso a las propiedades de los objetos activos.

- Matriz de valores de elemento.

  Un contrato para un conjunto de interfaces COM que se encuentra en un único objeto COM de servicio. Cuando se crea un servicio, que se identifica mediante un GUID, defina el conjunto de interfaces COM que lleva a cabo el servicio. Objetos COM usan servicios para comunicarse entre sí.

  solución de grupo de proyectos relacionados con la que un usuario trabaja.

  Un diseñador que se puede usar independientemente del tipo de proyecto de diseñador estándar. Todos los diseñadores estándares deben introducir su información de generador de editores en el registro. El IDE, a continuación, puede crear una instancia del diseñador cada vez que se abre un archivo con una extensión específica. Deben guardar los datos en un archivo.

  editor estándar de Editor que se puede usar independientemente de cualquier tipo de proyecto determinado. Estos editores tienen EditorFactories registrado en el registro. Esto permite que el IDE localizar e invocar el editor.

  editor del sistema operativo estándar de inclusión no es específico de Visual Studio. Está registrado con las claves conocidas de Win32 (por ejemplo, el Explorador de Win32 sabe cómo invocar). Si se puede incrustar un editor de este tipo, el editor aún aparece en su lugar en el IDE. En caso contrario, se crea una ventana de nivel superior independiente para dichos editores.

  contenedor de subcontextos un `IVsUserContext` objeto vinculado a un contenedor de contextos. El objeto contiene palabras clave de búsqueda, **F1** palabras clave y los atributos de una selección dentro de un componente IDE. Ejemplos de subcontexto incluyen un comando en una ventana de herramientas o una palabra clave en un editor.

  Ventana de la herramienta de lista de tareas que se implementa mediante el IDE y muestra una lista de tareas activas.

  nombre común de búfer de texto para el objeto `VSTextBuffer`.

  Nombre común de vista de texto para el objeto `VSTextView`.

  componente de un componente de nivel superior de la herramienta que funciona como una ventana emergente modal, coordinación estrechamente con la interfaz de usuario del IDE. Al igual que los componentes de nivel superior independientes, componentes de nivel superior de la herramienta también deben coordinar modalidad y servicios de bucle de mensajes con el IDE.

  objeto de un VSPackage del componente de nivel superior que administra una ventana de nivel superior no modal en lugar del área cliente de una ventana del IDE. Implementan componentes de nivel superior la `IOleComponent` interfaz para aprovechar las ventajas de servicios de bucle de mensajes, como el acceso en tiempo de inactividad.

  Interfaz de usuario un objeto VSPackage activo de que está visible y que tiene actualmente el foco.

  Objeto de COM de una jerarquía de interfaz de usuario que implementa el `IVsUIHierarchy` interfaz para permitir la visualización de una jerarquía. La ventana de jerarquía de la interfaz de usuario se implementa el `ISelectionContainer` para actualizar la ventana Propiedades de la interfaz; otras ventanas de tipo de proyecto pueden utilizar esta implementación, si lo desea.

  Tabla de comandos de Visual Studio VSCT. El archivo .vsct contiene información sobre la selección de ubicación y los comportamientos de menús, barras de herramientas y comandos en formato XML.

  VSPackage un componente instalable de software que extiende el IDE de Visual Studio al contribuir con uno o varios de los siguientes elementos: interfaz de usuario, servicios, tipos de proyecto o editor o diseñador. Un VSPackage consta de un objeto COM que implementa el `IVsPackage` interfaz y uno o varios otros objetos COM que implementan otras interfaces para admitir la selección y otras características. Además, un VSPackage tiene los requisitos del Registro específica.