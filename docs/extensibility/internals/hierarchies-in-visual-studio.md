---
title: Jerarquías en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0774c4a7ad9686b02501bed80a060519f5a500f3
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510415"
---
# <a name="hierarchies-in-visual-studio"></a>Jerarquías en Visual Studio
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) muestra un proyecto como un *jerarquía*. En el IDE, una jerarquía es un árbol de nodos, donde cada nodo tiene un conjunto de propiedades asociadas. Un *jerarquía del proyecto* es un contenedor que contiene elementos de proyecto, las relaciones de los elementos y las propiedades asociadas y los comandos.  
  
 En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], administrar las jerarquías de proyecto mediante el uso de la interfaz de la jerarquía, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz redirige los comandos que se invoca desde elementos de proyecto a la ventana de jerarquía adecuada en lugar del controlador de comandos estándar.  
  
## <a name="project-hierarchies"></a>Jerarquías de proyecto  
 Cada jerarquía del proyecto contiene elementos que puede ver y editar. Estos elementos varían según el tipo de proyecto. Por ejemplo, un proyecto de base de datos podría contener los procedimientos almacenados, vistas de base de datos y tablas de base de datos. Por otro lado, un proyecto de lenguaje de programación, probablemente incluya archivos de origen y archivos de recursos para los mapas de bits y cuadros de diálogo. Las jerarquías se pueden anidar, que proporciona cierta flexibilidad adicional cuando se crea una jerarquía de proyectos.  
  
 Cuando se crea un nuevo tipo de proyecto, el tipo de proyecto controla el conjunto completo de los elementos que se pueden editar en ella. Sin embargo, los proyectos pueden contener elementos para los que no tienen compatibilidad de edición. Por ejemplo, los proyectos de Visual C++ pueden contener archivos HTML, aunque Visual C++ no proporciona ningún editor personalizado para el tipo de archivo HTML.  
  
 Las jerarquías de administran la persistencia de los elementos que contienen. La implementación de la jerarquía debe controlar las propiedades especiales que afectan a la persistencia de los elementos dentro de la jerarquía. Por ejemplo, si los elementos representan objetos en un repositorio en lugar de archivos, la implementación de la jerarquía debe controlar la persistencia de esos objetos. El propio IDE dirige la jerarquía para guardar los elementos de acuerdo con la entrada del usuario, pero el IDE no controla las acciones necesarias para guardar los elementos. En su lugar, el proyecto está en el control.  
  
 Cuando un usuario abre un elemento en un editor, la jerarquía que controla el elemento está seleccionada y se convierte en la jerarquía activa. La jerarquía seleccionada determina el conjunto de comandos disponibles para que actúe en el elemento. Seguimiento de foco del usuario de esta manera, permite la jerarquía reflejar el contexto del usuario actual.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)   
 [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Muestras de VSSDK](http://aka.ms/vs2015sdksamples)