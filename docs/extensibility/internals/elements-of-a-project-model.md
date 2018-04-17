---
title: Elementos de un modelo de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4933e73df93c1f8a3bcf62e03b6883c0096f1d8f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="elements-of-a-project-model"></a>Elementos de un modelo de proyecto
Las interfaces y las implementaciones de todos los proyectos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comparten una estructura básica: el modelo de proyecto para el tipo de proyecto. En el modelo de proyecto, que es el VSPackage que está desarrollando, crear objetos que cumplen con sus decisiones de diseño y de trabajo junto con la funcionalidad global proporcionada por el IDE. Aunque puede controlar cómo se guarda un elemento de proyecto, por ejemplo, no se controla notificación que se debe conservar un archivo. Cuando un usuario coloca el foco en un elemento de proyecto abierto y elige **guardar** en el **archivo** menú en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menú barras, el código del tipo de proyecto debe interceptar el comando desde el IDE, el archivo, se conservan y Enviar notificación volver al IDE que ya no se modifique el archivo.  
  
 El paquete de VS interactúa con el IDE a través de servicios que proporcionan acceso a las interfaces IDE. Por ejemplo, a través de determinados servicios, monitor y la ruta de comandos y proporciona información de contexto para las selecciones realizadas en el proyecto. Servicios proporciona toda la funcionalidad IDE global necesaria para el VSPackage. Para obtener más información acerca de los servicios, vea [Cómo: obtener un servicio](../../extensibility/how-to-get-a-service.md).  
  
 Otras consideraciones de implementación:  
  
-   Un modelo de proyecto solo puede contener más de un tipo de proyecto.  
  
-   Tipos de proyecto y los generadores de operador de proyecto se registran por separado con GUID.  
  
-   Cada proyecto debe tener un archivo de plantilla o el Asistente para inicializar el nuevo archivo de proyecto cuando un usuario crea un nuevo proyecto a través de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario. Por ejemplo, el [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] plantillas inicializar lo que finalmente se convierten en .vcproj (archivos).  
  
 En la siguiente ilustración muestra las interfaces principales, servicios y objetos que componen una implementación normal del proyecto. Puede utilizar la aplicación auxiliar de aplicación, HierUtil7, para crear los objetos subyacentes y otro reutilizable de programación. Para obtener más información acerca de la aplicación auxiliar de aplicación de HierUtil7, consulte [no en la compilación: utilizar clases de proyecto HierUtil7 para implementar un tipo de proyecto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![Gráfico del modelo de proyecto de Studio Visual](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
modelo de proyecto  
  
 Para obtener más información acerca de las interfaces y servicios que se muestran en el diagrama anterior y otras interfaces opcionales no se incluye en el diagrama, vea [componentes principales del proyecto de modelo](../../extensibility/internals/project-model-core-components.md).  
  
 Proyectos puede admitir comandos y, por tanto, debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para participar en el enrutamiento de comandos a través del contexto de comando GUID.  
  
## <a name="see-also"></a>Vea también  
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [No en la compilación: usar clases de proyectos de HierUtil7 para implementar un tipo de proyecto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Componentes principales del proyecto de modelo](../../extensibility/internals/project-model-core-components.md)   
 [Crear instancias de Project mediante generadores de proyectos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Cómo: obtener un servicio](../../extensibility/how-to-get-a-service.md)   
 [Creación de tipos de proyecto](../../extensibility/internals/creating-project-types.md)