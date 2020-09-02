---
title: Glosario de Visual Studio SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c189c4c9e06d224d7cef296a2c39e732cbc29f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538720"
---
# <a name="visual-studio-sdk-glossary"></a>Glosario de Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este glosario proporciona definiciones de los términos que se usan en la [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] documentación de.  
  
## <a name="terms"></a>Términos  
 de comprobación  
 Aplicación de utilidad, controlador u otro software agregado a una aplicación principal. En el entorno de desarrollo integrado (IDE) de Visual Studio, un complemento es una aplicación basada en automatización que amplía las capacidades del IDE.  
  
 modelo de automatización  
 El modelo de automatización, conocido en versiones anteriores de Visual Studio como el modelo de extensibilidad, es una interfaz de programación que proporciona acceso a las rutinas subyacentes que controlan el IDE. Los complementos, los asistentes y las macros usan objetos en el modelo de automatización para controlar o extender la funcionalidad del IDE.  
  
 contexto de la interfaz de usuario de comandos  
 Asociación de un GUID con la visibilidad de un comando o elemento de la interfaz de usuario como, por ejemplo, una barra de herramientas. El contexto de la interfaz de usuario de comandos no se adjunta a una ventana.  
  
 El contexto de la interfaz de usuario de comandos se puede usar para:  
  
- Asignar un GUID a una barra de herramientas que aparece cuando se activa una ventana determinada.  
  
- Asigne un GUID a la disponibilidad de un comando sin tener que cargar o ejecutar un VSPackage.  
  
- Asigne un GUID para que afecte al enlace de teclado activo.  
  
- Asigne un GUID para activar la grabación de macros.  
  
- Asigne un GUID para activar el modo de depuración o para alternar entre el modo de diseño y el de ejecución en un editor.  
  
  component  
  Parte del software que se puede convertir en parte de la funcionalidad de una aplicación sin que esa aplicación tenga información preexistente sobre la implementación del software. La comunicación entre un componente y una aplicación se realiza exclusivamente a través de las interfaces de estilo OLE.  
  
  Administrador de componentes  
  Un servicio, `SOleComponentManager` , que proporciona servicios de coordinación que no son de interfaz de usuario para los componentes de nivel superior. El `SOleComponentManager` servicio implementa la `IOleComponentManager` interfaz.  
  
  Administrador de interfaz de usuario de componentes  
  Un servicio, `SOleComponentUIManager` , que proporciona servicios de coordinación de la interfaz de usuario. El `SOleComponentUIManager` servicio implementa las `IOleComponentUIManager` interfaces y `IOleInPlaceComponentUIManager` .  
  
  contenedor de contexto  
  `IVsUserContext`Objeto (objeto com) asociado a un componente de entorno. Este objeto contiene palabras clave de búsqueda, palabras clave de F1 y atributos relacionados con el componente. Los contenedores contextuales también señalan a cualquier bolsas de subcontexto que esté vinculada a ellos.  
  
  proveedor de contexto  
  Componente en el IDE que tiene asociado un contenedor de contextos. Estos componentes incluyen una ventana de herramientas, un editor o una jerarquía de proyecto.  
  
  designer  
  Interfaz de programación que permite a los usuarios manipular los elementos de la interfaz de usuario (formularios, botones y otros controles).  
  
  DocData  
  Objeto COM que encapsula los datos subyacentes de un documento en un mundo donde hay separación de documento/vista (por ejemplo, en el caso del editor de texto, esto sería el búfer de texto subyacente a todas las vistas del editor de texto). Si el EditorFactory no proporciona este objeto, el IDE fabricará uno en su nombre. La responsabilidad de este objeto es administrar la persistencia de datos y la semántica de uso compartido para varias vistas a lo largo de este mismo `DocData` . Si el `DocData` objeto admite la `IOleCommandTarget` interfaz, se incluirá en el enrutamiento de comandos de UIShell.  
  
  DocObject  
  Tecnología que se usa para hospedar la interfaz de usuario en un marco proporcionado por el host. Más concretamente, este término hace referencia a cualquier inserción que admita las `IOleDocument` interfaces relacionadas con y. Esta tecnología tiene muchas aplicaciones posibles, como un detalle de implementación de documentos COM, ventanas de herramientas en Visual Basic 5,0, diseñadores de ActiveX en Visual Basic 6,0, etc.  
  
  documento  
  Se usa para hacer referencia genéricamente al documento en su totalidad, tanto el como `DocData` el `DocView` . Por ejemplo, un DocumentFrame contiene `DocView` , pero también conserva una referencia a `DocData` para controlar la persistencia.  
  
  DocView  
  El DocObject/incrustación/ventana con el que el usuario interactúa para ver y manipular el subyacente `DocData` . Tenga en cuenta que los usuarios no aprovechan la separación de documento/vista que forma parte del diseño de la `DocObject` interfaz. Los usuarios usan un DocObject completo para actuar como una vista en lugar de usar una noción más abstracta (y menos formalizada) de los datos subyacentes conocidos como `DocData` . `DocView` los objetos siempre se incrustan con objetos de marco de documento (ventanas secundarias MDI) del IDE.  
  
  DTE  
  El `DTE` objeto (extensibilidad de herramientas de desarrollo) es el punto de acceso más alto en el modelo de automatización de Visual Studio, que permite automatizar y extender el IDE mediante programación.  
  
  Ventana de Ayuda dinámica  
  Ventana de herramientas implementada por el IDE y muestra una lista de palabras clave de búsqueda o temas de la ayuda de F1.  
  
  editor  
  Código (clase, CLSID) que implementa `DocView` . También implementa `DocData` si se admite la separación de la vista o los datos.  
  
  extensión  
  Característica que modifica, Personaliza o agrega a un IDE. Las extensiones se crean mediante el modelo de automatización o VSPackages.  
  
  editor externo  
  Un editor que no es específico del IDE, como Microsoft Word. Se ha registrado a través de sus propios mecanismos y se puede usar fuera del IDE. Si este editor se puede incrustar, aparece dentro de una ventana en el IDE. Si no se puede incrustar, se crea una ventana de nivel superior independiente.  
  
  Jerarquía  
  Árbol de nodos, cada nodo asociado a un conjunto de propiedades.  
  
  componente de nivel superior independiente  
  Componente que usa una ventana de nivel superior no modal y puede funcionar eficazmente como una ventana de aplicación independiente, pero se implementa como un objeto en proceso. Por lo tanto, un componente de nivel superior independiente debe coordinar los servicios de la modalidad y el bucle de mensajes con el IDE. Los objetos en proceso no tienen su propio bucle de mensajes.  
  
  proveedor de información  
  El proveedor de información es un módulo que puede buscar palabras clave y devolver una lista de temas, en forma de `IVsUserContextItem` objetos. Para proporcionar F1 y elementos de palabra clave de búsqueda para el proveedor de información, registre el archivo de ayuda compilado (. HxS) con el sistema. Los temas de ayuda de estos archivos se usan para proporcionar la lista de temas que se muestran en la ventana Ayuda dinámica y se muestra si un usuario presiona F1.  
  
  componente en contexto  
  Objeto VSPackage que implementa la `IOleInPlaceComponent` interfaz para administrar una ventana que está contenida visualmente dentro de una ventana de documento propiedad del IDE. Los componentes en contexto no participan en la combinación de menús OLE estándar; en su lugar, integran sus elementos de la interfaz de usuario en el IDE.  
  
  Hay dos tipos de componentes en contexto: componentes en contexto y controles de componentes.  
  
  Los componentes en contexto integrados tienen menús, barras de herramientas y comandos que se integran estrechamente en la interfaz de usuario del IDE, que aparecen como si estuvieran compilados directamente en el IDE.  
  
  Los controles de componentes no tienen ninguno de sus propios elementos de interfaz de usuario integrados en el IDE; en su lugar, usan los menús, comandos y barras de herramientas del IDE. Por ejemplo, el comando Bold podría usarse para poner en negrita una palabra seleccionada dentro de un control de texto enriquecido incrustado en un formulario. Sin embargo, los controles de componentes pueden solicitar que se muestren elementos de interfaz de usuario específicos del componente instalados dinámicamente.  
  
  servicio de lenguaje  
  Conjunto de objetos que permite a los desarrolladores de VSPackage implementar características de los editores de código de idioma del equipo, como el marcado y la coloración de texto.  
  
  Proyecto de archivos varios  
  Proyecto usado para alojar archivos abiertos que no están en ningún proyecto. La lista de elementos de este proyecto no se conserva.  
  
  proyecto  
  Los proyectos se componen de objetos de jerarquía o de objetos COM que implementan la `IVsHierarchy` interfaz.  
  
  diseñador o editor específico del proyecto  
  Un diseñador que no se puede usar independientemente del tipo de proyecto. Todos los diseñadores específicos del proyecto deben escribir su información de generador de editores en el registro. Después, el IDE puede crear una instancia del diseñador cada vez que se abre un determinado tipo de archivo en un proyecto determinado.  
  
  ventana tipo de proyecto  
  Ventana que realiza un seguimiento constante del elemento y la jerarquía del proyecto actualmente activo desde el contexto de selección global. Las ventanas tipo de proyecto usan el `SVsTrackSelectionEx` servicio para avisar al IDE de los cambios y para mostrar comentarios al usuario. Explorador de soluciones es un ejemplo de una ventana de tipo de proyecto.  
  
  Propiedades (ventana)  
  Anteriormente explorador de propiedades.  
  
  proyectos basados en referencia  
  Proyecto que no requiere que los archivos del proyecto estén en el mismo directorio. En su lugar, el propio proyecto almacena y mantiene las referencias a los archivos de otros directorios no relacionados.  
  
  tabla de documentos en ejecución  
  Estructura interna por la que el IDE mantiene la lista de todos los documentos abiertos actualmente. Esta lista incluye todos los documentos abiertos en memoria independientemente de si los documentos se están editando actualmente. Un documento es cualquier elemento que se guarda, incluidos los procedimientos almacenados abiertos en un editor, los archivos de un proyecto o el archivo de proyecto principal (por ejemplo, *. vcproj).  
  
  contexto de selección  
  Datos que forman parte de los detalles de todas las ventanas del IDE y que se usan para realizar el seguimiento de las selecciones activas. El contexto de selección consta de:  
  
- Puntero a la `IVsHierarchy` interfaz de la jerarquía del proyecto  
  
- Identificador de elemento del elemento de proyecto.  
  
- Puntero a la `ISelectionContainer` interfaz que proporciona acceso a las propiedades de los objetos activos.  
  
- Matriz de valores de elemento.  
  
  service  
  Un contrato para un conjunto de interfaces COM que residen en un único objeto COM. Cuando se crea un servicio, que se identifica mediante un GUID, se define el conjunto de interfaces COM que realiza el servicio. Los objetos COM utilizan los servicios para comunicarse entre sí.  
  
  solución  
  Grupo de proyectos relacionados con los que trabaja un usuario.  
  
  diseñador estándar  
  Un diseñador que se puede usar de manera independiente del tipo de proyecto. Todos los diseñadores estándar deben escribir su información de generador de editores en el registro. Después, el IDE puede crear una instancia del diseñador cada vez que se abre un archivo con una extensión específica. Los datos deben conservarse en un archivo.  
  
  editor estándar  
  Editor que se puede usar independientemente de cualquier tipo de proyecto concreto. Estos editores tienen EditorFactories registrados en el registro. Esto permite al IDE ubicar e invocar el editor.  
  
  Editor de sistema operativo estándar  
  Incrustación que no es específica de Visual Studio. Se registra con las conocidas claves de Win32 (por ejemplo, el explorador de Win32 sabe cómo invocar). Si este editor se puede incrustar, el editor seguirá apareciendo en su lugar en el IDE. De lo contrario, se crea una ventana de nivel superior independiente para dichos editores.  
  
  contenedor de subcontextos  
  `IVsUserContext`Objeto vinculado a un contenedor de contexto. Este objeto contiene palabras clave de búsqueda, palabras clave F1 y atributos para una selección dentro de un componente IDE. Los ejemplos de subcontexto incluyen un comando en una ventana de herramientas o una palabra clave en un editor.  
  
  Lista de tareas  
  Ventana de herramientas implementada por el IDE y muestra una lista de tareas activas.  
  
  búfer de texto  
  Nombre común del objeto `VSTextBuffer` .  
  
  Vista de texto  
  Nombre común del objeto `VSTextView` .  
  
  componente de nivel superior de la herramienta  
  Componente que funciona como una ventana emergente no modal y que se coordina estrechamente con la interfaz de usuario del IDE. Al igual que los componentes de nivel superior independientes, los componentes de nivel superior de la herramienta también deben coordinar los servicios de la modalidad y del bucle de mensajes con el IDE.  
  
  componente de nivel superior  
  Objeto VSPackage que administra una ventana de nivel superior no modal en lugar del área cliente de una ventana IDE. Los componentes de nivel superior implementan la `IOleComponent` interfaz para aprovechar los servicios de bucle de mensajes, como el acceso al tiempo de inactividad.  
  
  Interfaz de usuario activa  
  Objeto VSPackage que es visible y que actualmente tiene el foco.  
  
  Jerarquía de la interfaz de usuario  
  Objeto COM que implementa la `IVsUIHierarchy` interfaz para permitir la presentación de una jerarquía. La ventana jerarquía de la interfaz de usuario implementa la `ISelectionContainer` interfaz para actualizar el ventana Propiedades; otras ventanas de tipo de proyecto pueden utilizar esta implementación, si se desea.  
  
  VSCT  
  Tabla de comandos de Visual Studio. El archivo. Vsct contiene información sobre la ubicación y los comportamientos de los menús, las barras de herramientas y los comandos en formato XML.  
  
  VSPackage  
  Un fragmento de software instalable que extiende el IDE de Visual Studio contribuyendo a uno o varios de los siguientes elementos: interfaz de usuario, servicios, tipos de proyecto o editor o diseñador. Un VSPackage está compuesto de un objeto COM que implementa la `IVsPackage` interfaz y uno o más objetos com que implementan otras interfaces para admitir la selección y otras características. Además, un VSPackage tiene requisitos de registro específicos.
