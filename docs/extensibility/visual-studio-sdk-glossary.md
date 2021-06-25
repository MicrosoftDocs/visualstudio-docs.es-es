---
title: Visual Studio glosario del SDK | Microsoft Docs
description: Este glosario proporciona definiciones de los términos que se usan en la documentación Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 49e91a64220882eea196819a1860052dc871bec4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905428"
---
# <a name="visual-studio-sdk-glossary"></a>glosario del SDK de Visual Studio
Este glosario proporciona definiciones de los términos que se usan en la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentación.

## <a name="terms"></a>Términos
 complemento Aplicación de utilidad, controlador u otro software agregado a una aplicación principal. En el Visual Studio de desarrollo integrado (IDE), un complemento es una aplicación basada en Automation que amplía las funcionalidades del IDE.

 modelo de automatización El modelo de automatización, conocido en versiones anteriores de Visual Studio como modelo de extensibilidad, es una interfaz de programación que proporciona acceso a las rutinas subyacentes que impulsan el IDE. Los complementos, asistentes y macros usan objetos del modelo de automatización para controlar o ampliar la funcionalidad del IDE.

 contexto de interfaz de usuario de comando Asociación de un GUID con la visibilidad de un comando o elemento de interfaz de usuario, como una barra de herramientas. El contexto de la interfaz de usuario de comandos es diferente del contexto de selección, ya que no está asociado a una ventana.

 El contexto de la interfaz de usuario de comandos se puede usar para:

- Asigne un GUID a una barra de herramientas que aparece cuando se activa una ventana determinada.

- Asigne un GUID a la disponibilidad de un comando sin tener que cargar o ejecutar un VSPackage.

- Asigne un GUID para que afecte al enlace de claves activo.

- Asigne un GUID para activar la grabación de macros.

- Asigne un GUID para activar el modo de depuración o para alternar entre el modo de diseño y ejecución en un editor.

  componente Fragmento de software que se puede convertir en parte de la funcionalidad de una aplicación sin que esa aplicación tenga información preexistida sobre la implementación del software. La comunicación entre un componente y una aplicación se hace únicamente a través de interfaces de estilo OLE.

  Administrador de componentes Un servicio, , que proporciona servicios de coordinación de interfaces que no son de `SOleComponentManager` usuario para componentes de nivel superior. El `SOleComponentManager` servicio implementa la interfaz `IOleComponentManager` .

  Administrador de interfaz de usuario de componentes Un servicio, `SOleComponentUIManager` , que proporciona servicios de coordinación de la interfaz de usuario. El `SOleComponentUIManager` servicio implementa las `IOleComponentUIManager` `IOleInPlaceComponentUIManager` interfaces y .

  bolsa de contexto `IVsUserContext` Un objeto (objeto COM) asociado a un componente de entorno. Este objeto contiene palabras clave de búsqueda, **palabras clave F1** y atributos relacionados con el componente. Las bolsas de contexto apuntan además a cualquier bolsa de subcontexto que esté vinculada a ellas.

  proveedor de contexto Un componente del IDE que tiene asociado un bolsa de contexto. Estos componentes incluyen una ventana de herramientas, un editor o una jerarquía de proyectos.

  diseñador Una interfaz de programación que permite a los usuarios manipular elementos de la interfaz de usuario (formularios, botones y otros controles).

  DocData Un objeto COM que encapsula los datos subyacentes de un documento en un mundo donde hay separación entre documentos y vistas (por ejemplo, en el caso del editor de texto, este sería el búfer de texto subyacente a todas las vistas del editor de texto). Si EditorFactory no proporciona este objeto, el IDE fabrica uno en su nombre. La responsabilidad de este objeto es administrar la persistencia de los datos y la semántica de uso compartido para varias vistas sobre este mismo `DocData` . Si el `DocData` objeto admite la interfaz , se incluye en el enrutamiento de comandos de `IOleCommandTarget` UIShell.

  Tecnología DocObject que se usa para hospedar la interfaz de usuario dentro de un marco proporcionado por el host. Más concretamente, este término hace referencia a cualquier inserción que admita las `IOleDocument` interfaces y relacionadas. Esta tecnología tiene muchas aplicaciones potenciales, como un detalle de implementación de documentos COM, ventanas de herramientas en Visual Basic 5.0, diseñadores ActiveX en Visual Basic 6.0, y así sucesivamente.

  documento Usado para hacer referencia genéricamente al documento en su conjunto: y `DocData` `DocView` . Por ejemplo, un elemento DocumentFrame contiene , pero también conserva una referencia `DocView` a para controlar la `DocData` persistencia.

  DocView DocObject/Embedding/WindowPane con el que el usuario interactúa para ver y manipular el `DocData` subyacente. Los usuarios no aprovechan la separación entre documentos y vistas que forma parte del diseño `DocObject` de la interfaz. Los usuarios usan un objeto DocObject completo para actuar como una vista en lugar de usar una noción más abstracta (y menos formalizada) de los datos subyacentes conocidos como `DocData` . `DocView` Los objetos siempre se incrustan con objetos de marco de documento (ventanas secundarias MDI) del IDE.

  DTE El objeto (extensibilidad de las herramientas de desarrollo) es el punto de acceso más alto del modelo de automatización de Visual Studio, que permite automatizar y ampliar mediante programación `DTE` el IDE.

  Ventana de ayuda dinámica Ventana de herramientas que implementa el IDE y muestra una lista de palabras clave de búsqueda o temas de Ayuda **F1.**

  editor Code (clase, CLSID) que implementa `DocView` . También implementa si se `DocData` admite la separación de datos y la vista.

  extensión Característica que modifica, personaliza o agrega a un IDE. Las extensiones se crean mediante el modelo de automatización o VSPackages.

  editor externo Un editor que no es específico del IDE, como Microsoft Word. Se ha registrado a través de sus propios mecanismos y se puede usar fuera del IDE. Si este editor se puede incrustar, aparece dentro de una ventana en el IDE. Si no se puede incrustar, se crea una ventana de nivel superior independiente.

  jerarquía Árbol de nodos, cada nodo asociado a un conjunto de propiedades.

  componente de nivel superior independiente Un componente que usa una ventana de nivel superior no modelo y puede funcionar eficazmente como una ventana de aplicación independiente, pero que se implementa como un objeto en proceso. Por lo tanto, un componente de nivel superior independiente debe coordinar los servicios de modalidad y bucle de mensajes con el IDE. Los objetos en proceso no tienen su propio bucle de mensajes.

  proveedor de información El proveedor de información es un módulo que puede buscar palabras clave y devolver una lista de temas, en forma de `IVsUserContextItem` objetos . Para proporcionar **F1 y elementos** de palabra clave de búsqueda para el proveedor de información, registre el archivo de Ayuda compilado (*. HxS*) con el sistema. Los temas de Ayuda de estos archivos proporcionan la lista de temas que se muestran en la ventana Ayuda dinámica y muestran si un usuario presiona **F1.**

  componente in-place Un objeto VSPackage que implementa la interfaz para administrar una ventana que se encuentra visualmente dentro de una ventana de documento propiedad `IOleInPlaceComponent` del IDE. Los componentes en contexto no participan en la combinación de menús OLE estándar; en su lugar, integran sus elementos de interfaz de usuario en el IDE.

  Hay dos tipos de componentes en su lugar: componentes en posición cableados y controles de componentes.

  Los componentes en contexto cableados tienen menús, barras de herramientas y comandos que se integran estrechamente en la interfaz de usuario del IDE, y aparecen como si se hubieran integrado directamente en el IDE.

  Los controles de componentes no tienen ninguno de sus propios elementos de interfaz de usuario integrados en el IDE; en su lugar, usan los menús, comandos y barras de herramientas del IDE. Por ejemplo, el comando Negrita podría usarse para negrita a una palabra seleccionada dentro de un control de texto enriquecido insertado en un formulario. Sin embargo, los controles de componente pueden solicitar que se muestren los elementos de interfaz de usuario específicos del componente instalados dinámicamente.

  servicio de lenguaje Un conjunto de objetos que permite a los desarrolladores de VSPackage implementar características de editores de código de idioma del equipo, como el marcado de texto y la coloración.

  Proyecto de archivos varios Que se usa para hospedar archivos abiertos que no están en ningún proyecto. La lista de elementos de este proyecto no se conserva.

  Los proyectos de proyecto se realizan en objetos de jerarquía u objetos COM que implementan la `IVsHierarchy` interfaz .

  Diseñador o editor específico del proyecto Un diseñador que no se puede usar independientemente del tipo de proyecto. Todos los diseñadores específicos del proyecto deben escribir su información de Editor Factory en el Registro. A continuación, el IDE puede crear instancias del diseñador cada vez que se abre un determinado tipo de archivo en un proyecto determinado.

  ventana de tipo de proyecto Ventana que realiza un seguimiento constante de la jerarquía y el elemento del proyecto actualmente activos desde el contexto de selección global. Las ventanas de tipo proyecto usan el servicio para alertar al IDE de los cambios `SVsTrackSelectionEx` y mostrar comentarios al usuario. Explorador de soluciones es un ejemplo de una ventana de tipo proyecto.

  ventana Propiedades Anteriormente, Explorador de propiedades.

  proyectos basados en referencia Proyecto que no requiere que los archivos del proyecto se encontrarán en el mismo directorio. En su lugar, el propio proyecto almacena y mantiene las referencias a archivos de otros directorios no relacionados.

  ejecutar la tabla de documentos Estructura interna por la que el IDE mantiene la lista de todos los documentos abiertos actualmente. La lista incluye todos los documentos abiertos en memoria, independientemente de si los documentos se están editando actualmente. Un documento es cualquier elemento que se guarda, incluidos los procedimientos almacenados abiertos en un editor, los archivos de un proyecto o el archivo de proyecto principal (por ejemplo, el archivo *.vcproj).

  contexto de selección Datos que forman parte de los detalles de cada ventana del IDE y se usa para realizar un seguimiento de las selecciones activas. El contexto de selección consta de:

- Puntero a la `IVsHierarchy` interfaz de la jerarquía del proyecto

- Identificador de elemento del elemento de proyecto.

- Puntero a la `ISelectionContainer` interfaz que proporciona acceso a las propiedades de los objetos activos.

- Matriz de valores de elemento.

  servicio Un contrato para un conjunto de interfaces COM que reside en un único objeto COM. Al crear un servicio, que se identifica mediante un GUID, se define el conjunto de interfaces COM que lleva a cabo el servicio. Los objetos COM usan servicios para comunicarse entre sí.

  solución Grupo de proyectos relacionados con los que trabaja un usuario.

  diseñador estándar Un diseñador que se puede usar independientemente del tipo de proyecto. Todos los diseñadores estándar deben escribir su información de Editor Factory en el Registro. A continuación, el IDE puede crear instancias del diseñador cada vez que se abre un archivo con una extensión específica. Los datos deben conservarse en un archivo.

  Editor estándar que se puede usar independientemente de cualquier tipo de proyecto determinado. Estos editores tienen EditorFactories registrados en el Registro. Esto permite que el IDE busque e invoque el editor.

  Editor del sistema operativo estándar Una inserción que no es Visual Studio específico. Se registra mediante las conocidas claves win32 (por ejemplo, el Explorador de Win32 sabe cómo invocar). Si se puede incrustar un editor de este tipo, el editor todavía aparece en su lugar en el IDE. De lo contrario, se crea una ventana de nivel superior independiente para dichos editores.

  subcontext bag Un `IVsUserContext` objeto vinculado a un bolsa de contexto. El objeto contiene palabras clave de búsqueda, **palabras clave F1** y atributos para una selección dentro de un componente ide. Algunos ejemplos de subcontexto incluyen un comando en una ventana de herramientas o una palabra clave en un editor.

  Lista de tareas Ventana de herramientas que implementa el IDE y muestra una lista de tareas activas.

  búfer de texto Nombre común del objeto `VSTextBuffer` .

  Vista de texto Nombre común del objeto `VSTextView` .

  componente de nivel superior de la herramienta Componente que funciona como una ventana emergente de modelado, que se coordina estrechamente con la interfaz de usuario del IDE. Al igual que los componentes independientes de nivel superior, los componentes de nivel superior de la herramienta también deben coordinar los servicios de modalidad y bucle de mensajes con el IDE.

  componente de nivel superior Un objeto VSPackage que administra una ventana de nivel superior modelada en lugar del área cliente de una ventana ide. Los componentes de nivel superior implementan la interfaz para aprovechar los servicios de bucle de `IOleComponent` mensajes, como el acceso al tiempo de inactividad.

  Ui active Un objeto VSPackage que está visible y actualmente tiene el foco.

  Jerarquía de interfaz de usuario Un objeto COM que implementa `IVsUIHierarchy` la interfaz para permitir la presentación de una jerarquía. La ventana de jerarquía de interfaz de usuario implementa la interfaz para actualizar el ventana Propiedades; otras ventanas de tipo proyecto pueden `ISelectionContainer` usar esta implementación, si lo desea.

  Tabla de comandos Visual Studio VSCT. El archivo .vsct contiene información sobre la ubicación y los comportamientos de los menús, las barras de herramientas y los comandos en formato XML.

  VSPackage Un fragmento de software instalable que extiende el IDE de Visual Studio mediante la contribución de uno o varios de los siguientes elementos: interfaz de usuario, servicios, tipos de proyecto o editor/diseñador. Un VSPackage consta de un objeto COM que implementa la interfaz y uno o varios otros objetos COM que implementan otras interfaces para admitir la selección `IVsPackage` y otras características. Además, un VSPackage tiene requisitos de registro específicos.
