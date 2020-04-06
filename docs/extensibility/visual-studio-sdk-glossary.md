---
title: Glosario del SDK de Visual Studio (Visual Studio SDK Glossary) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 332e606e689e9394f2fcdc8cbc902e2d4a6e5ab5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698166"
---
# <a name="visual-studio-sdk-glossary"></a>Glosario del SDK de Visual Studio
Este glosario proporciona definiciones para [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] los términos que se utilizan en la documentación.

## <a name="terms"></a>Términos
 complemento Una aplicación de utilidad, controlador u otro software agregado a una aplicación principal. En el entorno de desarrollo integrado (IDE) de Visual Studio, un complemento es una aplicación basada en automatización que amplía las capacidades del IDE.

 Modelo de automatización El modelo de automatización, conocido en versiones anteriores de Visual Studio como el modelo de extensibilidad, es una interfaz de programación que le da acceso a las rutinas subyacentes que controlan el IDE. Complementos, asistentes y macros usan objetos en el modelo de automatización para controlar o ampliar la funcionalidad del IDE.

 contexto de interfaz de usuario de comandos Asociación de un GUID con la visibilidad de un comando o elemento de interfaz de usuario, como una barra de herramientas. El contexto de la interfaz de usuario de comandos es diferente del contexto de selección, ya que no está asociado a una ventana.

 El contexto de la interfaz de usuario de comandos se puede utilizar para:

- Asigne un GUID a una barra de herramientas que aparece cuando se activa una ventana determinada.

- Asigne un GUID a la disponibilidad de un comando sin tener que cargar o ejecutar un VSPackage.

- Asigne un GUID para afectar al enlace de claves activo.

- Asigne un GUID para activar la grabación de macros.

- Asigne un GUID para activar el modo de depuración o para alternar entre el modo de diseño y de ejecución en un editor.

  componente Pieza de software que se puede hacer parte de la funcionalidad de una aplicación sin que esa aplicación tenga ninguna información preexistente sobre la implementación del software. La comunicación entre un componente y una aplicación es únicamente a través de interfaces de estilo OLE.

  administrador de componentes Un servicio, `SOleComponentManager`, que proporciona servicios de coordinación de interfaz de usuario para componentes de nivel superior. El `SOleComponentManager` servicio implementa `IOleComponentManager` la interfaz.

  administrador de interfaz `SOleComponentUIManager`de usuario de componentes Un servicio, que proporciona servicios de coordinación de interfaz de usuario. El `SOleComponentUIManager` servicio implementa `IOleComponentUIManager` `IOleInPlaceComponentUIManager` las interfaces y.

  bolsa de `IVsUserContext` contexto Un objeto (objeto COM) asociado a un componente de entorno. Este objeto contiene palabras clave de búsqueda, palabras clave **F1** y atributos relacionados con el componente. Las bolsas de contexto apuntan además a cualquier bolsa de subcontexto que esté vinculada a ellas.

  proveedor de contexto Un componente del IDE que tiene asociada una bolsa de contexto. Estos componentes incluyen una ventana de herramientas, un editor o una jerarquía de proyectos.

  diseñador Una interfaz de programación que permite a los usuarios manipular elementos de la interfaz de usuario (formularios, botones y otros controles).

  DocData Un objeto COM que encapsula los datos subyacentes de un documento en un mundo donde hay separación de documento/vista (por ejemplo, en el caso del editor de texto, este sería el búfer de texto subyacente a todas las vistas del editor de texto). Si EditorFactory no proporciona este objeto, el IDE fabrica uno en su nombre. La responsabilidad de este objeto es administrar la persistencia de datos `DocData`y la semántica de uso compartido para varias vistas sobre este mismo archivo . Si `DocData` el objeto `IOleCommandTarget` admite la interfaz, se incluye en el enrutamiento de comandos de UIShell.

  Tecnología DocObject utilizada para hospedar la interfaz de usuario dentro de un marco proporcionado por el host. Más específicamente, este término se refiere `IOleDocument` a cualquier incrustación que soporte las interfaces relacionadas. Esta tecnología tiene muchas aplicaciones potenciales, como un detalle de implementación de documentos COM, ventanas de herramientas en Visual Basic 5.0, diseñadores ActiveX en Visual Basic 6.0, etc.

  documento Utilizado para referirse genéricamente al documento `DocData` en `DocView`su conjunto, tanto el archivo . Por ejemplo, un DocumentFrame contiene un `DocView`, pero `DocData` también conserva una referencia a la para controlar la persistencia.

  DocView El DocObject/Embedding/WindowPane con el que el usuario `DocData`interactúa para ver y manipular el archivo . Los usuarios no aprovechan la separación Documento/Vista que forma parte del diseño de la `DocObject` interfaz. Los usuarios utilizan un DocObject completo para actuar como una vista en lugar de `DocData`utilizar una noción más abstracta (y menos formalizada) de datos subyacentes conocidos como . `DocView`los objetos siempre se incrustan con objetos de marco de documento (ventanas secundarias MDI) del IDE.

  DTE `DTE` El objeto (Extensibilidad de herramientas de desarrollo) es el punto de acceso superior del modelo de automatización de Visual Studio, que permite automatizar y ampliar mediante programación el IDE.

  Ventana Ayuda dinámica Ventana herramienta implementada por el IDE y muestra una lista de palabras clave de búsqueda o temas de Ayuda **de F1.**

  editor Code (clase, CLSID) `DocView`que implementa el archivo . También se `DocData` implementa si se admite la vista y la separación de datos.

  extensión Una característica que modifica, personaliza o agrega a un IDE. Crear extensiones mediante el modelo de automatización o VSPackages.

  editor externo Un editor que no es específico del IDE, como Microsoft Word. Se ha registrado a través de sus propios mecanismos y se puede utilizar fuera del IDE. Si este editor se puede incrustar, aparece dentro de una ventana en el IDE. Si no se puede incrustar, se crea una ventana de nivel superior independiente.

  jerarquía árbol de nodos, cada nodo asociado a un conjunto de propiedades.

  componente independiente de nivel superior Componente A que utiliza una ventana de nivel superior no quede no quedado y puede funcionar eficazmente como una ventana de aplicación independiente, pero se implementa como un objeto en proceso. Por lo tanto, un componente de nivel superior independiente debe coordinar la modalidad y los servicios de bucle de mensajes con el IDE. Los objetos en proceso no tienen su propio bucle de mensajes.

  proveedor de información El proveedor de información es un módulo que puede buscar `IVsUserContextItem` palabras clave y devolver una lista de temas, en forma de objetos. Para proporcionar **F1** y elementos de palabraclave de búsqueda para el proveedor de información, registre el archivo de Ayuda compilado (*. HxS*) con el sistema. Los temas de Ayuda de estos archivos proporcionan la lista de temas que se muestran en la ventana Ayuda dinámica y muestran si un usuario presiona **F1**.

  Componente in situ Un objeto VSPackage `IOleInPlaceComponent` que implementa la interfaz para administrar una ventana que se encuentra visualmente dentro de una ventana de documento propiedad del IDE. Los componentes in situ no participan en la combinación de menús OLE estándar; en su lugar, integran sus elementos de interfaz de usuario en el IDE.

  Hay dos tipos de componentes in situ: componentes in situ cableados y controles de componentes.

  Los componentes in situ cableados tienen menús, barras de herramientas y comandos que se integran estrechamente en la interfaz de usuario del IDE, que aparecen como si estuvieran integrados directamente en el IDE.

  Los controles de componentes no tienen ninguno de sus propios elementos de interfaz de usuario integrados en el IDE; en su lugar, utilizan los menús, comandos y barras de herramientas del IDE. Por ejemplo, el comando Negrita se podría utilizar para poner en negrita una palabra seleccionada dentro de un control de texto enriquecido incrustado en un formulario. Sin embargo, los controles de componentes pueden solicitar que se muestren los elementos de interfaz de usuario específicos del componente instalados dinámicamente.

  Servicio de lenguaje Un conjunto de objetos que permite a los desarrolladores de VSPackage implementar características de editores de código de lenguaje de equipo, como el marcado de texto y colorear.

  Proyecto de proyecto de archivos varios utilizado para albergar archivos abiertos que no están en ningún proyecto. La lista de elementos de este proyecto no se conserva.

  Los proyectos de proyecto se componen de objetos de jerarquía u objetos COM que implementan la `IVsHierarchy` interfaz.

  Diseñador o editor específico del proyecto Un diseñador que no se puede usar independientemente del tipo de proyecto. Todos los diseñadores específicos del proyecto deben introducir su información de Editor Factory en el registro. A continuación, el IDE puede crear instancias del diseñador cada vez que se abre un determinado tipo de archivo en un proyecto determinado.

  ventana de tipo de proyecto Una ventana que realiza un seguimiento constante de la jerarquía de proyectos activa y el elemento desde el contexto de selección global. Las ventanas de `SVsTrackSelectionEx` tipo de proyecto usan el servicio para alertar al IDE de los cambios y mostrar comentarios al usuario. El Explorador de soluciones es un ejemplo de una ventana de tipo de proyecto.

  Ventana Propiedades Anteriormente Navegador de propiedades.

  proyectos basados en referencias Project que no requiere que los archivos del proyecto estén en el mismo directorio. En su lugar, las referencias a archivos de otros directorios no relacionados se almacenan y mantienen mediante el propio proyecto.

  tabla de documentos en ejecución Estructura interna mediante la cual el IDE mantiene la lista de todos los documentos abiertos actualmente. La lista incluye todos los documentos abiertos en la memoria, independientemente de si los documentos se están editando actualmente. Un documento es cualquier elemento que se guarda, incluidos los procedimientos almacenados abiertos en un editor, los archivos de un proyecto o el archivo de proyecto principal (por ejemplo, el archivo *.vcproj).

  contexto de selección Datos que forman parte del detalle de cada ventana del IDE y se utiliza para realizar un seguimiento de las selecciones activas. El contexto de selección consta de:

- Puntero a `IVsHierarchy` la interfaz de la jerarquía del proyecto

- Identificador de elemento del elemento de proyecto.

- Puntero a `ISelectionContainer` la interfaz que proporciona acceso a las propiedades de los objetos activos.

- Matriz de valores de elemento.

  servicio Un contrato para un conjunto de interfaces COM que reside en un único objeto COM. Cuando se crea un servicio, que se identifica mediante un GUID, se define el conjunto de interfaces COM que lleva a cabo el servicio. Los objetos COM utilizan servicios para comunicarse entre sí.

  solución Grupo de proyectos relacionados con los que un usuario trabaja.

  Diseñador estándar Un diseñador que se puede usar independientemente del tipo de proyecto. Todos los diseñadores estándar deben introducir su información de Editor Factory en el registro. A continuación, el IDE puede crear instancias del diseñador cada vez que se abre un archivo con una extensión específica. Los datos deben persistir en un archivo.

  Editor estándar que se puede utilizar independientemente de cualquier tipo de proyecto en particular. Estos editores tienen EditorFactories registrados en el registro. Esto permite que el IDE localice e invoque el editor.

  Editor de SO estándar Una incrustación que no es específica de Visual Studio. Se registra mediante las conocidas claves Win32 (por ejemplo, el Explorador de Win32 sabe cómo invocar). Si se puede incrustar un editor de este tipo, el editor sigue apareciendo en su lugar en el IDE. De lo contrario, se crea una ventana de nivel superior independiente para estos editores.

  bolsa de `IVsUserContext` subcontexto Un objeto vinculado a una bolsa de contexto. El objeto contiene palabras clave de búsqueda, palabras clave **F1** y atributos para una selección dentro de un componente IDE. Entre los ejemplos de subcontexto se incluyen un comando en una ventana de herramientas o una palabra clave en un editor.

  Lista de tareas Ventana de herramientas implementada por el IDE y muestra una lista de tareas activas.

  búfer de texto Nombre `VSTextBuffer`común para el objeto .

  Vista de texto Nombre `VSTextView`común del objeto .

  componente de nivel superior de herramienta Componente A que funciona como una ventana emergente no basada en modelos, coordinando estrechamente con la interfaz de usuario del IDE. Al igual que los componentes independientes de nivel superior, los componentes de nivel superior de herramientas también deben coordinar la modalidad y los servicios de bucle de mensajes con el IDE.

  Componente de nivel superior Un objeto VSPackage que administra una ventana de nivel superior no esquemética en lugar del área de cliente de una ventana IDE. Los componentes de `IOleComponent` nivel superior implementan la interfaz para aprovechar los servicios de bucle de mensajes, como el acceso al tiempo de inactividad.

  Interfaz de usuario activa Un objeto VSPackage que está visible y actualmente tiene el foco.

  Jerarquía de interfaz de `IVsUIHierarchy` usuario Un objeto COM que implementa la interfaz para permitir la visualización de una jerarquía. La ventana de jerarquía `ISelectionContainer` de interfaz de usuario implementa la interfaz para actualizar la ventana Propiedades; otras ventanas de tipo de proyecto pueden usar esta implementación, si lo desea.

  Tabla de comandos de Visual Studio de VSCT. El archivo .vsct contiene información sobre la ubicación y los comportamientos de menús, barras de herramientas y comandos en formato XML.

  VSPackage Una pieza de software instalable que extiende el IDE de Visual Studio aportando uno o varios de los siguientes elementos: interfaz de usuario, servicios, tipos de proyecto o editor o diseñador. Un VSPackage consta de un objeto `IVsPackage` COM que implementa la interfaz y uno o varios otros objetos COM que implementan otras interfaces para admitir la selección y otras características. Además, un VSPackage tiene requisitos de registro específicos.
