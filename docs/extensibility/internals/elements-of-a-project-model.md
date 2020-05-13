---
title: Elementos de un modelo de proyecto ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708521"
---
# <a name="elements-of-a-project-model"></a>Elementos de un modelo de proyecto
Las interfaces e implementaciones [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de todos los proyectos en comparten una estructura básica: el modelo de proyecto para el tipo de proyecto. En el modelo de proyecto, que es el VSPackage que está desarrollando, cree objetos que cumplan con las decisiones de diseño y trabajar junto con la funcionalidad global proporcionada por el IDE. Aunque controla cómo se conserva un elemento de proyecto, por ejemplo, no controla la notificación de que se debe conservar un archivo. Cuando un usuario coloca el foco en un elemento de proyecto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] abierto y elige **Guardar** en el menú **Archivo** de la barra de menús, el código de tipo de proyecto debe interceptar el comando desde el IDE, conservar el archivo y enviar una notificación al IDE de que el archivo ya no se cambia.

 El VSPackage interactúa con el IDE a través de servicios que proporcionan acceso a las interfaces IDE. Por ejemplo, a través de determinados servicios, puede supervisar y enrutar comandos y proporcionar información de contexto para las selecciones realizadas en el proyecto. Toda la funcionalidad IDE global necesaria para el VSPackage es proporcionada por los servicios. Para obtener más información acerca de los servicios, vea [Cómo: Obtener un servicio](../../extensibility/how-to-get-a-service.md).

 Otras consideraciones de implementación:

- Un único modelo de proyecto puede contener más de un tipo de proyecto.

- Los tipos de proyecto y los generadores de proyectos asistentes se registran de forma independiente con GUID.

- Cada proyecto debe tener un archivo de plantilla o asistente para inicializar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el nuevo archivo de proyecto cuando un usuario crea un nuevo proyecto a través de la interfaz de usuario. Por ejemplo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] las plantillas inicializan lo que finalmente se convierten en archivos .vcproj.

  En la ilustración siguiente se muestran las interfaces, los servicios y los objetos principales que componen una implementación de proyecto típica. Puede utilizar la aplicación `HierUtil7`auxiliar, , para crear los objetos subyacentes y otros reutilizables de programación. Para obtener más `HierUtil7` información acerca de la aplicación auxiliar, vea Usar clases de [proyecto HierUtil7 para implementar un tipo de proyecto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

  ![Gráfico del modelo](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") de proyecto de Visual Studio Modelo de proyecto

  Para obtener más información acerca de las interfaces y servicios enumerados en el diagrama anterior y otras interfaces opcionales no incluidas en el diagrama, vea [Componentes principales](../../extensibility/internals/project-model-core-components.md)del modelo de proyecto .

  Los proyectos pueden admitir comandos y, por lo tanto, deben implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para participar en el enrutamiento de comandos a través de los GUID de contexto de comando.

## <a name="see-also"></a>Vea también
- [Lista de verificación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Utilice las clases de proyecto HierUtil7 para implementar un tipo de proyecto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Componentes principales del modelo de proyecto](../../extensibility/internals/project-model-core-components.md)
- [Crear instancias de proyecto mediante fábricas de proyectos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Cómo: Obtener un servicio](../../extensibility/how-to-get-a-service.md)
- [Crear tipos de proyecto](../../extensibility/internals/creating-project-types.md)
