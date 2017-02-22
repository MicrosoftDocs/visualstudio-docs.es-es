---
title: "Elementos de un modelo de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos [Visual Studio SDK], consideraciones de implementación"
  - "modelos de proyecto"
  - "proyectos [Visual Studio SDK], elementos"
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Elementos de un modelo de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Las interfaces e implementaciones de todos los proyectos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comparten una estructura básica: el modelo de proyecto para el tipo de proyecto.  En el modelo de proyecto, que es el paquete VSPackage está desarrollando, se crean objetos que cumplen las decisiones de diseño y el trabajo así como la funcionalidad global proporcionada por el IDE.  Aunque se controla cómo se conserva un elemento de proyecto, por ejemplo, no controla la notificación que un archivo debe mantenerse.  Cuando un usuario coloca el foco en un elemento de proyecto abierto y elija **Guardar** en el menú de **Archivo** en la barra de menús de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , el código del tipo de proyecto debe interceptar el comando del IDE, guarda el archivo, y envía la notificación al IDE que el archivo se cambiado no más.  
  
 El paquete VSPackage interactúa con el IDE con los servicios que proporcionan acceso a las interfaces del IDE.  Por ejemplo, con servicios concretos, controla y enruta comandos y proporciona información de contexto para las opciones seleccionadas en el proyecto.  Toda la funcionalidad global del IDE necesaria para el paquete VSPackage es proporcionada por servicios.  Para obtener más información sobre los servicios, vea [Cómo: obtener un servicio](../../extensibility/how-to-get-a-service.md).  
  
 Otras consideraciones de implementación:  
  
-   un solo modelo de proyecto puede contener más de un tipo de proyecto.  
  
-   Registra los tipos de proyecto y los generadores involucradas de proyecto independientemente con Diferentes.  
  
-   Cada proyecto debe tener un archivo de plantilla o un asistente para inicializar el nuevo archivo de proyecto cuando un usuario crea un nuevo proyecto con la interfaz de usuario de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Por ejemplo, las plantillas de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] se inicializan qué se convierten en finalmente archivos .vcproj.  
  
 La ilustración siguiente se muestran las interfaces primarias, servicios, los objetos que componen una ejecución de proyecto típica.  Puede utilizar la aplicación auxiliar de la aplicación, HierUtil7, crear los objetos subyacentes y otra plancha de caldera de programación.  Para obtener más información sobre la aplicación auxiliar de la aplicación HierUtil7, vea [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/es-es/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![Gráfico del modelo de proyectos de Visual Studio](../../extensibility/internals/media/vsprojectmodel.png "vsProjectModel")  
modelo de proyecto  
  
 Para obtener más información sobre las interfaces y los servicios mostrados en el diagrama anterior, y otras interfaces opcionales no incluidos en el diagrama, vea [Componentes principales de modelo de proyecto](../../extensibility/internals/project-model-core-components.md).  
  
 Los proyectos pueden admitir comandos y por consiguiente deben implementar la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para participar en el enrutamiento de comandos con el contexto GUID de comando.  
  
## Vea también  
 [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/es-es/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Componentes principales de modelo de proyecto](../../extensibility/internals/project-model-core-components.md)   
 [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Cómo: obtener un servicio](../../extensibility/how-to-get-a-service.md)   
 [Creación de tipos de proyecto](../../extensibility/internals/creating-project-types.md)