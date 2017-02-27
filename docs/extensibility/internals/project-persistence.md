---
title: "Persistencia de un proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistencia, proyectos"
  - "persistencia de proyectos [Visual Studio SDK],"
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Persistencia de un proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Persistencia es un aspecto clave de diseño para el proyecto.  La mayoría de los proyectos utilizan los elementos que representan archivos; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] también admite los proyectos cuyo no\-archivo\-se basa datos.  Los archivos que pertenecen al proyecto y el archivo de proyecto deben guardarse.  El IDE indica al proyecto de salvarse o un elemento de proyecto.  
  
 Las plantillas de los proyectos se pasan al generador de proyectos.  Las plantillas deben admitir la inicialización de todos los elementos de proyecto según los requisitos de tipo de proyecto específico.  Estas plantillas se pueden guardar como archivos de proyecto y administrar más adelante con el IDE a través de la solución.  Para obtener más información, vea [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) y [Soluciones](../../extensibility/internals/solutions.md).  
  
 Los elementos de proyecto pueden ser basada en archivos o no\-archivo\-basados:  
  
-   Los elementos basados en archivos pueden ser locales o remotos.  En proyectos web en C\#, por ejemplo, las conexiones a archivos en un sistema remoto conservan localmente, como archivos propios conservan en el sistema remoto.  
  
-   los elementos No\-archivo\-basados pueden guardar elementos a una base de datos o un repositorio.  
  
## Modelos de confirmación  
 Después de decidir dónde se encuentran los elementos de proyecto, debe elegir el modelo adecuado de confirmación.  por ejemplo, en un modelo basado en archivos con los archivos locales, cada proyecto se puede guardar autónomo.  En un modelo del repositorio, puede guardar varios elementos en una transacción.  Para obtener más información, vea [Decisiones de diseño del tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md).  
  
 Para determinar las extensiones de nombre de archivo, los proyectos implementan la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> , que proporciona información habilitando el cliente de un objeto para implementar el diálogo de **Guardar como** cuadro\-que es, para completar la lista desplegable de **Guardar como tipo** y administrar la extensión de nombre de archivo inicial.  
  
 El IDE llama a la interfaz de `IPersistFileFormat` en el proyecto para indicar que el proyecto debe conservar sus elementos de proyecto adecuados.  Por consiguiente, el objeto posee todos los aspectos del archivo y formato.  Esto incluye el nombre de formato del objeto.  
  
 En caso de que no están archivos los elementos, `IPersistFileFormat` permanece cómo se conservan los elementos no\-archivo\-basados.  Los archivos de proyecto, como archivos de .vbp para los proyectos de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o archivos .vcproj para los proyectos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] , también deben guardarse.  
  
 Para acciones de guardar, el IDE examina la tabla en el documento \(RDT\) y la jerarquía pasa los comandos a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> e interfaces de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> .  El método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> se implementa para determinar si se ha modificado el elemento.  Si tiene, el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> se implementa para guardar el elemento modificado.  
  
 Los métodos de la interfaz de `IVsPersistHierarchyItem2` se utilizan para determinar si un elemento se puede recargar y, si el elemento puede ser, para recargarlo.  Además, el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> se puede implementar para proporcionar los elementos modificados que se descartarán sin guardar.  
  
## Vea también  
 [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)