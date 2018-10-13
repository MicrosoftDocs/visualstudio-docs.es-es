---
title: Glosario de Visual Studio SDK | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20310605ed73247958287903a8eb3926ee55ba1d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225555"
---
# <a name="visual-studio-sdk-glossary"></a>Glosario de Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este glosario proporciona definiciones de términos que se usan en el [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] documentación.  
  
## <a name="terms"></a>Términos  
 de comprobación  
 Una aplicación de utilidad, controlador u otro software que se agregan a una aplicación principal. En el entorno de desarrollo integrado (IDE) de Visual Studio, un complemento es una aplicación basada en la automatización que amplía las capacidades del IDE.  
  
 modelo de automatización  
 El modelo de automatización, conocido en versiones anteriores de Visual Studio como el modelo de extensibilidad, es una interfaz de programación que le proporciona acceso a las rutinas subyacentes que controlan el IDE. Complementos, asistentes y macros utilizan objetos en el modelo de automatización para controlar o extienden la funcionalidad del IDE.  
  
 contexto de interfaz de usuario de comandos  
 Asociación de un GUID con la visibilidad de un comando de la interfaz de usuario o un elemento, como una barra de herramientas. Contexto de interfaz de usuario de comandos es a diferencia de contexto de selección que no está asociado a una ventana.  
  
 Contexto de interfaz de usuario de comandos puede usarse para:  
  
-   Asignar un GUID a una barra de herramientas que aparece cuando se activa una ventana concreta.  
  
-   Asignar un GUID a la disponibilidad de un comando sin tener que cargar o ejecutar un paquete VSPackage.  
  
-   Asignar un GUID que afectan al enlace de teclado activos.  
  
-   Asignar un GUID para activar la grabación de macros.  
  
-   Asignar un GUID para activar el modo de depuración o para alternar entre el diseño y modo de ejecución en un editor.  
  
 component  
 Aplicación de software que se puede realizar parte de la funcionalidad de una aplicación sin esa aplicación que tiene toda la información sobre la implementación del software previamente existente. La comunicación entre un componente y una aplicación es únicamente a través de interfaces de estilo OLE.  
  
 Administrador de componentes  
 Un servicio, `SOleComponentManager`, que proporciona servicios de coordinación de interfaz de usuario que no son para los componentes de nivel superior. El `SOleComponentManager` servicio implementa el `IOleComponentManager` interfaz.  
  
 Administrador de componentes de interfaz de usuario  
 Un servicio, `SOleComponentUIManager`, que proporciona servicios de coordinación de interfaz de usuario. El `SOleComponentUIManager` servicio implementa el `IOleComponentUIManager` y `IOleInPlaceComponentUIManager` interfaces.  
  
 contenedor de contexto  
 Un `IVsUserContext` objeto (COM) asociado a un componente de entorno. Este objeto contiene palabras clave de búsqueda, palabras clave F1 y los atributos relacionados con el componente. Además punto bolsas de contexto a los contenedores de subcontexto que están vinculados a ellos.  
  
 proveedor de contexto  
 Un componente en el IDE que tiene un contenedor de contexto asociado con él. Estos componentes incluyen una ventana de herramientas, el editor o la jerarquía del proyecto.  
  
 designer  
 Una interfaz de programación que permite a los usuarios manipular los elementos de la interfaz de usuario (formularios, botones y otros controles).  
  
 DocData  
 Un objeto COM que encapsula los datos subyacentes de un documento en un mundo donde hay separación de documento/vista (por ejemplo, en el caso del editor de texto, esto sería el búfer de texto subyacente todas las vistas de editor de texto). Si el EditorFactory no proporciona este objeto, el IDE fabricará uno en su lugar. La responsabilidad de este objeto es administrar la persistencia de datos y la semántica de uso compartido para varias vistas a través de este mismo `DocData`. Si el `DocData` objeto admite el `IOleCommandTarget` interfaz, se incluirá en el enrutamiento de comandos de la UIShell.  
  
 DocObject  
 Tecnología utilizada para hospedar la interfaz de usuario dentro de un marco proporcionado por el host. Más concretamente, este término hace referencia a la inserción que admita la `IOleDocument` y las interfaces relacionadas. Esta tecnología tiene muchas posibles aplicaciones tales como un detalle de implementación de documentos de COM, ventanas de herramientas en Visual Basic 5.0, los diseñadores de ActiveX en Visual Basic 6.0 y así sucesivamente.  
  
 documento  
 Utilizado para hacer referencia genéricamente el documento en su totalidad, tanto el `DocData` y `DocView`. Por ejemplo, contiene un DocumentFrame un `DocView`, pero también mantiene una referencia a la `DocData` para controlar la persistencia.  
  
 DocView  
 El DocObject/Embedding/panel de la ventana con el que el usuario interactúa para ver y manipular subyacente `DocData`. Tenga en cuenta que los usuarios no aprovechar la separación de la vista del documento que forma parte de la `DocObject` diseño de interfaces. Los usuarios usar un DocObject todo para que actúe como una vista en lugar de usar una noción más abstractos (y menos formal) de datos subyacentes que se conoce como `DocData`. `DocView` los objetos siempre se incrustan con objetos de marco de documento (ventanas secundarias de MDI) del IDE.  
  
 DTE  
 La `DTE` objeto (extensibilidad de herramientas de desarrollo) es el punto de acceso de nivel superior en el modelo de automatización de Visual Studio, lo que permite automatizar y extender el IDE mediante programación.  
  
 Ventana de Ayuda dinámica  
 Ventana de herramientas que se implementa mediante el IDE y muestra una lista de la palabra clave de búsqueda o temas de Ayuda de F1.  
  
 editor  
 Código (clase, CLSID) que implementa el `DocView`. También implementa `DocData` si se admite la separación de datos o vista.  
  
 extensión  
 Una característica que se modifica, se personaliza, o se agrega a un IDE. Crear extensiones mediante el modelo de automatización o VSPackages.  
  
 editor externo  
 Un editor que no es específico para el IDE, como Microsoft Word. Se ha registrado a través de sus propios mecanismos y se puede usar fuera del IDE. Si se puede insertar este editor, aparece dentro de una ventana en el IDE. Si no se pueden insertar, se crea una ventana de nivel superior independiente.  
  
 jerarquía  
 Árbol de nodos, cada nodo asociado con un conjunto de propiedades.  
  
 componente de nivel superior independiente  
 Un componente que utiliza una ventana de nivel superior no modal y puede funcionar eficazmente como una ventana de aplicación independiente, pero se implementa como un objeto en proceso. Por lo tanto, un componente independiente de nivel superior debe coordinar modalidad y servicios de bucle de mensajes con el IDE. Objetos de proceso no tienen su propio bucle de mensajes.  
  
 proveedor de información  
 El proveedor de información es un módulo que se puede buscar palabras clave y devolver una lista de temas, en forma de `IVsUserContextItem` objetos. Para proporcionar elementos de palabra clave F1 y la búsqueda para el proveedor de información, registrar el archivo de Ayuda compilado (. HxS) con el sistema. Los temas de Ayuda de estos archivos se usan para proporcionar la lista de temas que se muestran en la ventana Ayuda dinámica y se muestra si un usuario presiona la tecla F1.  
  
 componente en contexto  
 Un objeto VSPackage que implemente la `IOleInPlaceComponent` interfaz para administrar una ventana que visualmente es dentro de una ventana de documento que pertenecen a la IDE. Los componentes en el contexto no participan en estándar OLE-combinación de menús; en su lugar se integran sus elementos de interfaz de usuario en el IDE.  
  
 Hay dos tipos de componentes en contexto: integrado en contexto los componentes y controles de componentes.  
  
 Integrado en contexto componentes tienen menús, barras de herramientas y comandos que se integran estrechamente en la interfaz de usuario del IDE, que aparecen como si se compilaron directamente en el IDE.  
  
 Controles de componentes no tiene ninguno de sus propios elementos de interfaz de usuario integrados en el IDE; en su lugar usan los menús, comandos y las barras de herramientas del IDE. Por ejemplo, podría usar el comando en negrita en negrita una palabra seleccionada dentro de un control de texto enriquecido incrustado en un formulario. Sin embargo, los controles de componentes pueden solicitar que se muestran elementos de interfaz de usuario específicos del componente instalados de forma dinámica.  
  
 servicio de lenguaje  
 Un conjunto de objetos que permite a los desarrolladores de VSPackage implementar características de editores de código de idioma de equipo, como texto de marcado y el coloreado.  
  
 Proyecto de archivos varios  
 Proyecto usado para los archivos abiertos de enrutamiento que no están en cualquier proyecto. No se conserva la lista de elementos de este proyecto.  
  
 proyecto  
 Los proyectos se componen de objetos de la jerarquía o COM, los objetos que implementan la `IVsHierarchy` interfaz.  
  
 específico del proyecto diseñador o editor  
 Un diseñador que no se puede usar con independencia del tipo de proyecto. Todos los diseñadores específicos del proyecto deben introducir su información de generador de editores en el registro. El IDE, a continuación, puede crear una instancia del diseñador cada vez que un determinado tipo de archivo se abre en un proyecto concreto.  
  
 ventana de tipo de proyecto  
 Una ventana que constantemente realiza el seguimiento de la jerarquía del proyecto activo actualmente y el elemento desde el contexto de la selección global. Tipo de proyecto windows utiliza el `SVsTrackSelectionEx` servicio alerte al IDE de cambios y para mostrar los comentarios al usuario. El Explorador de soluciones es un ejemplo de una ventana de tipo de proyecto.  
  
 Propiedades (ventana)  
 Explorador de propiedades anteriormente.  
  
 Proyectos basados en la referencia  
 Proyecto que no requieren los archivos del proyecto en el mismo directorio. En su lugar, las referencias a archivos de otros directorios no relacionados se almacenan y mantenidas por el propio proyecto.  
  
 tabla de documentos en ejecución  
 Estructura interna por el que el IDE mantiene la lista de todos los documentos abiertos actualmente. Esta lista incluye todos los documentos abiertos en memoria independientemente de si actualmente se está editando los documentos. Un documento es cualquier elemento que se guarda, incluidos los procedimientos almacenados que se abre en un editor, archivos de un proyecto o el archivo de proyecto principal (por ejemplo, el archivo *.vcproj).  
  
 Contexto de selección  
 Datos que forma parte de los detalles de cada ventana en el IDE y sirve para realizar un seguimiento de las selecciones activas. Contexto de selección se compone de:  
  
-   Puntero a la `IVsHierarchy` interfaz de la jerarquía del proyecto  
  
-   Identificador de elemento del elemento de proyecto.  
  
-   Puntero a la `ISelectionContainer` interfaz que proporciona acceso a las propiedades de los objetos activos.  
  
-   Matriz de valores de elemento.  
  
 service  
 Un contrato para un conjunto de interfaces COM que residen en un único objeto COM. Cuando se crea un servicio, que se identifica mediante un GUID, defina el conjunto de interfaces COM que lleva a cabo el servicio. Objetos COM usan servicios para comunicarse entre sí.  
  
 Solución  
 Grupo de proyectos relacionados con la que un usuario trabaja.  
  
 Diseñador estándar  
 Un diseñador que se puede usar independientemente del tipo de proyecto. Todos los diseñadores estándares deben introducir su información de generador de editores en el registro. El IDE, a continuación, puede crear una instancia del diseñador cada vez que se abre un archivo con una extensión específica. Deben guardar los datos en un archivo.  
  
 editor estándar  
 Editor que se puede usar independientemente de cualquier tipo de proyecto determinado. Estos editores tienen EditorFactories registrado en el registro. Esto permite que el IDE localizar e invocar el editor.  
  
 editor estándar de sistema operativo  
 Una inserción que no es Visual Studio específico. Está registrado con las claves conocidas de Win32 (por ejemplo, el Explorador de Win32 sabe cómo invocar). Si se puede incrustar un editor de este tipo, el editor aún aparecerá en su lugar en el IDE. En caso contrario, se crea una ventana de nivel superior independiente para dichos editores.  
  
 contenedor de subcontextos  
 Un `IVsUserContext` objeto vinculado a un contenedor de contextos. Este objeto contiene los atributos de una selección dentro de un componente IDE, palabras clave F1 y palabras clave de búsqueda. Ejemplos de subcontexto incluyen un comando en una ventana de herramientas o una palabra clave en un editor.  
  
 Lista de tareas  
 Ventana de herramientas que se implementa mediante el IDE y muestra una lista de tareas activas.  
  
 Búfer de texto  
 Nombre común para el objeto `VSTextBuffer`.  
  
 Vista de texto  
 Nombre común para el objeto `VSTextView`.  
  
 componente de nivel superior de la herramienta  
 Un componente que funciona como una ventana emergente modal, coordinación estrechamente con la interfaz de usuario del IDE. Al igual que los componentes de nivel superior independientes, componentes de nivel superior de la herramienta también deben coordinar modalidad y servicios de bucle de mensajes con el IDE.  
  
 componente de nivel superior  
 Un objeto VSPackage que administra una ventana de nivel superior no modal en lugar del área cliente de una ventana del IDE. Implementan componentes de nivel superior la `IOleComponent` interfaz para aprovechar las ventajas de servicios de bucle de mensajes, como el acceso en tiempo de inactividad.  
  
 Interfaz de usuario activo  
 Un objeto VSPackage que está visible y que tiene actualmente el foco.  
  
 Jerarquía de la interfaz de usuario  
 Un objeto COM que implementa el `IVsUIHierarchy` interfaz para permitir la visualización de una jerarquía. La ventana de jerarquía de la interfaz de usuario se implementa el `ISelectionContainer` para actualizar la ventana Propiedades de la interfaz; otras ventanas de tipo de proyecto pueden utilizar esta implementación, si lo desea.  
  
 VSCT  
 Tabla de comandos de Visual Studio. El archivo .vsct contiene información sobre la selección de ubicación y los comportamientos de menús, barras de herramientas y comandos en formato XML.  
  
 VSPackage  
 Un componente instalable de software que extiende el IDE de Visual Studio al contribuir con uno o varios de los siguientes: interfaz de usuario, servicios, tipos de proyecto o editor o diseñador. Un VSPackage consta de un objeto COM que implementa el `IVsPackage` interfaz y uno o varios otros objetos COM que implementan otras interfaces para admitir la selección y otras características. Además, un VSPackage tiene los requisitos del Registro específica.

