---
title: Elementos de un modelo de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e14086ea395ffe65a52f47d0bfaa320fb19bc8f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910093"
---
# <a name="elements-of-a-project-model"></a>Elementos de un modelo de proyecto
Las interfaces y las implementaciones de todos los proyectos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comparten una estructura básica: el modelo de proyecto para el tipo de proyecto. En el modelo de proyecto, que es el VSPackage que se va a desarrollar, crear objetos que cumplen con sus decisiones de diseño y trabaje en conjunto con la funcionalidad global proporcionada por el IDE. Aunque controla cómo se conserva un elemento de proyecto, por ejemplo, no controlar notificaciones que se debe conservar un archivo. Cuando un usuario coloca el foco en un elemento de proyecto abierto y elige **guardar** en el **archivo** menú en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menú barras, debe interceptar el comando desde el IDE, conservará el archivo de código del tipo de proyecto y Enviar notificación al IDE que ya no se modifica el archivo.

 El VSPackage interactúa con el IDE a través de servicios que proporcionan acceso a las interfaces IDE. Por ejemplo, a través de determinados servicios, monitor y la ruta de comandos y proporciona información de contexto para las selecciones realizadas en el proyecto. Todas las funciones del IDE global necesaria para el VSPackage proporciona servicios. Para obtener más información acerca de los servicios, vea [Cómo: Obtener un servicio](../../extensibility/how-to-get-a-service.md).

 Otras consideraciones de implementación:

- Un modelo de proyecto solo puede contener más de un tipo de proyecto.

- Tipos de proyecto y los generadores de proyectos de operador se registran por separado con GUID.

- Cada proyecto debe tener un archivo de plantilla o el Asistente para inicializar el nuevo archivo de proyecto cuando un usuario crea un nuevo proyecto a través de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la interfaz de usuario. Por ejemplo, el [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] plantillas inicializar lo que finalmente se convierten en .vcproj (archivos).

  La ilustración siguiente muestra las interfaces principales, servicios y objetos que componen una implementación típica del proyecto. Puede usar la aplicación auxiliar de la aplicación, `HierUtil7`, para crear los objetos subyacentes y otra programación reutilizable. Para obtener más información sobre la `HierUtil7` aplicación auxiliar de la aplicación, consulte [HierUtil7 Use clases de proyecto para implementar un tipo de proyecto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

  ![Gráfico del modelo de proyecto de Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") modelo de proyecto

  Para obtener más información acerca de las interfaces y servicios que se enumeran en el diagrama anterior y otras interfaces opcionales no se incluye en el diagrama, vea [componentes principales del modelo de proyecto](../../extensibility/internals/project-model-core-components.md).

  Los proyectos pueden admitir los comandos y, por tanto, debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para participar en el enrutamiento de comandos a través del GUID de contexto de comando.

## <a name="see-also"></a>Vea también
- [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Utilizar clases de proyecto de HierUtil7 para implementar un tipo de proyecto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Componentes principales de modelo de proyecto](../../extensibility/internals/project-model-core-components.md)
- [Crear instancias de proyecto mediante generadores de proyectos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Cómo: Obtener un servicio](../../extensibility/how-to-get-a-service.md)
- [Crear tipos de proyecto](../../extensibility/internals/creating-project-types.md)
