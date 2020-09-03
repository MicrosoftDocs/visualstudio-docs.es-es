---
title: Diseño de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6e9eaf69be62b38a880b07fd8eb51cfc9c256a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195072"
---
# <a name="command-design"></a>Diseño de comandos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cuando se agrega un comando a un VSPackage, debe especificar dónde va a aparecer, Cuándo está disponible y cómo debe controlarse.  
  
## <a name="defining-commands"></a>Definir comandos  
 Para definir nuevos comandos, incluya un archivo de tabla de comandos de Visual Studio (. Vsct) en el proyecto de VSPackage. Si ha creado un VSPackage mediante la plantilla de paquete de Visual Studio, el proyecto incluye uno de estos archivos. Para obtener más información, consulta [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio combina todos los archivos. Vsct que encuentra para que pueda mostrar los comandos. Dado que estos archivos son distintos del archivo binario de VSPackage, Visual Studio no tiene que cargar el paquete para encontrar los comandos. Para obtener más información, vea [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio usa el <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> atributo de registro para definir los comandos y los recursos del menú. Para obtener más información, vea [implementación](../../extensibility/internals/command-implementation.md).  
  
 Los comandos se pueden cambiar en tiempo de ejecución de varias maneras diferentes. Pueden mostrarse u ocultarse, habilitarse o deshabilitarse. Pueden mostrar texto o iconos distintos o contener valores distintos. Se puede realizar una gran cantidad de personalización antes de que Visual Studio cargue el VSPackage. Para obtener más información, vea [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Controladores de comandos  
 Al crear un comando, debe proporcionar un controlador de eventos para ejecutar el comando. Si el usuario selecciona el comando, se debe enrutar correctamente. El enrutamiento de un comando significa enviarlo al VSPackage correcto para habilitarlo o deshabilitarlo, ocultarlo o mostrarlo, y ejecutarlo si el usuario decide hacerlo. Para obtener más información, vea [algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Entorno de comandos de Visual Studio  
 Visual Studio puede hospedar cualquier número de VSPackages y cada uno puede contribuir con su propio conjunto de comandos. El entorno muestra solo los comandos que son adecuados para la tarea actual. Para obtener más información, vea [objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)y [disponibilidad](../../extensibility/internals/command-availability.md) .  
  
 Un VSPackage que define nuevos comandos, menús, barras de herramientas o menús contextuales proporciona la información de comandos a Visual Studio en el momento de la instalación a través de las entradas del registro que hacen referencia a los recursos de los ensamblados nativos o administrados. Cada recurso hace referencia a un archivo de recursos de datos binarios (. CTO), que se genera al compilar un archivo de tabla de comandos de Visual Studio (. Vsct). Esto permite a Visual Studio proporcionar conjuntos de comandos, menús y barras de herramientas combinados sin tener que cargar cada VSPackage instalado.  
  
### <a name="command-organization"></a>Organización de comandos  
 El entorno coloca los comandos por grupo, prioridad y menú.  
  
- Los grupos son colecciones lógicas de comandos relacionados, por ejemplo, el grupo de comandos **cortar**, **copiar**y **pegar** . Los grupos son los comandos que aparecen en los menús.  
  
- Prioridad determina el orden en que aparecen los comandos individuales en un grupo en el menú.  
  
- Los menús actúan como contenedores para los grupos.  
  
  El entorno predefine algunos comandos, grupos y menús. Para obtener más información, vea selección de ubicación de la barra de herramientas, el [grupo y el comando predeterminado](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Un comando se puede asignar a un grupo primario. El grupo primario controla la posición del comando en la estructura de menú principal y en el cuadro de diálogo **personalizar** . Un comando puede aparecer en varios grupos; por ejemplo, un comando puede estar en el menú principal, en un menú contextual y en una barra de herramientas. Para obtener más información, vea [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>enrutamiento de comandos  
 El proceso de invocar y enrutar comandos para VSPackages difiere del proceso de llamada a métodos en instancias de objeto.  
  
 El entorno enruta los comandos secuencialmente desde el contexto de comandos más interno (local), que se basa en la selección actual, hasta el contexto más externo (global). El primer contexto que puede ejecutar el comando es el que lo controla. Para obtener más información, vea [algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md).  
  
 En la mayoría de los casos, el entorno controla los comandos mediante la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Dado que el esquema de enrutamiento de comandos permite que muchos objetos diferentes controlen los comandos, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> se puede implementar mediante cualquier número de objetos; entre ellos, los controles ActiveX de Microsoft, las implementaciones de vistas de ventanas, los objetos de documento, las jerarquías de proyecto y los propios objetos VSPackage (para los comandos globales). En algunos casos especializados, por ejemplo, los comandos de enrutamiento en una jerarquía, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> se debe implementar la interfaz.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Title|Descripción|  
|-----------|-----------------|  
|[Implementación](../../extensibility/internals/command-implementation.md)|Describe cómo implementar comandos en un VSPackage.|  
|[Disponibilidad](../../extensibility/internals/command-availability.md)|Describe cómo el contexto de Visual Studio determina qué comandos están disponibles.|  
|[Algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md)|Describe cómo la arquitectura de enrutamiento de comandos de Visual Studio permite que los comandos se controlen mediante VSPackages diferentes.|  
|[Instrucciones sobre la selección de ubicación](../../extensibility/internals/command-placement-guidelines.md)|Sugiere cómo colocar comandos en el entorno de Visual Studio.|  
|[Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Describe cómo los paquetes VSPackage pueden aprovechar mejor la arquitectura de comandos de Visual Studio.|  
|[Ubicación predeterminada de comando, grupo y barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Describe cómo los paquetes VSPackage pueden usar mejor los comandos que se incluyen en Visual Studio.|  
|[Administración de VSPackages](../../extensibility/managing-vspackages.md)|Describe cómo Visual Studio carga VSPackages.|  
|[Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Proporciona información sobre los archivos. Vsct basados en XML, que se utilizan para describir el diseño y la apariencia de los comandos en VSPackages.|
