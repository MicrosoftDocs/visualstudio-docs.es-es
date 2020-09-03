---
title: Elementos de un modelo de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf847e35878dc84bb32fe81053c01c23e565fc4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708521"
---
# <a name="elements-of-a-project-model"></a>Elementos de un modelo de proyecto
Las interfaces y las implementaciones de todos los proyectos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comparten una estructura básica: el modelo de proyecto para el tipo de proyecto. En el modelo de proyecto, que es el VSPackage que está desarrollando, cree objetos que cumplan sus decisiones de diseño y colaboren con la funcionalidad global que proporciona el IDE. Aunque controle el modo en que se conserva un elemento de proyecto, por ejemplo, no controla la notificación de que se debe guardar un archivo. Cuando un usuario coloca el foco en un elemento de proyecto abierto y elige **Guardar** en el menú **archivo** en la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra de menús, el código de tipo de proyecto debe interceptar el comando desde el IDE, conservar el archivo y enviar la notificación de vuelta al IDE para que el archivo ya no se cambie.

 El VSPackage interactúa con el IDE a través de los servicios que proporcionan acceso a las interfaces IDE. Por ejemplo, a través de servicios concretos, los comandos se supervisan y enrutan y proporcionan información de contexto para las selecciones realizadas en el proyecto. Todos los servicios proporcionan toda la funcionalidad global del IDE necesaria para el VSPackage. Para obtener más información acerca de los servicios, consulte [Cómo: obtener un servicio](../../extensibility/how-to-get-a-service.md).

 Otras consideraciones de implementación:

- Un modelo de proyecto único puede contener más de un tipo de proyecto.

- Los tipos de proyecto y los generadores de proyectos de operador se registran independientemente de los GUID.

- Cada proyecto debe tener un archivo de plantilla o un asistente para inicializar el nuevo archivo de proyecto cuando un usuario crea un nuevo proyecto a través de la interfaz de usuario [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Por ejemplo, las [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] plantillas inicializan lo que finalmente se convierte en archivos. vcproj.

  En la ilustración siguiente se muestran las interfaces, los servicios y los objetos principales que componen una implementación de proyecto típica. Puede usar la aplicación auxiliar de aplicaciones, `HierUtil7` , para crear los objetos subyacentes y otros tipos de programación. Para obtener más información sobre la `HierUtil7` aplicación auxiliar de aplicaciones, vea [usar clases de proyecto de HierUtil7 para implementar un tipo de proyecto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

  ![Gráfico del modelo de proyecto de Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Modelo de proyecto

  Para obtener más información sobre las interfaces y los servicios enumerados en el diagrama anterior y otras interfaces opcionales no incluidas en el diagrama, vea [Project Model Core Components](../../extensibility/internals/project-model-core-components.md).

  Los proyectos pueden admitir comandos y, por lo tanto, deben implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para participar en el enrutamiento de comandos a través de los GUID de contexto de comandos.

## <a name="see-also"></a>Consulte también
- [Lista de comprobación: crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Usar clases de proyecto de HierUtil7 para implementar un tipo de proyecto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Componentes principales del modelo de proyecto](../../extensibility/internals/project-model-core-components.md)
- [Creación de instancias de proyecto mediante el uso de generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Cómo: obtener un servicio](../../extensibility/how-to-get-a-service.md)
- [Crear tipos de proyecto](../../extensibility/internals/creating-project-types.md)
