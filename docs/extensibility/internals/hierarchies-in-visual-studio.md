---
title: "Jerarqu&#237;as en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "jerarquías, IDE de Visual Studio"
  - "IDE, jerarquías"
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Jerarqu&#237;as en Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muestra un proyecto como una *jerarquía*.  En el IDE, una jerarquía es un árbol de nodos, donde cada nodo tiene un conjunto de propiedades asociadas.  *Una jerarquía del proyecto* es un contenedor que contiene los elementos de proyecto, las relaciones de los elementos, y las propiedades asociadas y comandos de elementos.  
  
 En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se administran las jerarquías mediante la interfaz de la jerarquía, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>del proyecto.  La interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> redirige comandos que invoque de elementos a la ventana adecuada de la jerarquía en lugar de controlador estándar del comando.  
  
## Jerarquías de proyecto  
 Cada jerarquía del proyecto contiene elementos que puede ver y editar.  Estos elementos varían en función del tipo de proyecto.  Por ejemplo, un proyecto de base de datos podría contener procedimientos almacenados, las vistas de base de datos, y las tablas de base de datos.  Un proyecto del lenguaje de programación, por otro lado, incluirá probablemente los archivos de código fuente y archivos de recursos para los mapas de bits y cuadros de diálogo.  Las jerarquías pueden anidarse, que proporciona cierta flexibilidad adicional cuando se crea una jerarquía del proyecto.  
  
 Cuando se crea un nuevo tipo de proyecto, el tipo de proyecto controla todo el conjunto de elementos que se pueden editar en él.  Sin embargo, los proyectos pueden contener elementos para los que no admiten la edición.  Por ejemplo, los proyectos de Visual C\+\+ pueden contener archivos HTML, aunque Visual C\+\+ no proporciona ningún editor personalizado para el tipo de archivo HTML.  
  
 Las jerarquías administran la persistencia de elementos contenedores.  La implementación de la jerarquía debe controlar cualquier propiedad especial que afecte a la persistencia de los elementos de la jerarquía.  Por ejemplo, si los elementos representan objetos en un repositorio en lugar de archivos, la implementación de la jerarquía debe controlar la persistencia de esos objetos.  El IDE propio dirige la jerarquía para guardar elementos de acuerdo con los datos proporcionados por el usuario, pero este no controla ninguna acción necesaria para guardar esos elementos.  En su lugar, el proyecto esté en el control.  
  
 Cuando un usuario abre un elemento de un editor, la jerarquía que controla ese elemento está seleccionado y se convierte en la jerarquía activo.  La jerarquía seleccionado determina el conjunto de comandos disponibles para representar en el elemento.  El foco de usuario de seguimiento de esta manera permite a la jerarquía para reflejar el contexto del usuario actual.  
  
## Vea también  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)   
 [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Muestras de VSSDK](../../misc/vssdk-samples.md)