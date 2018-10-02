---
title: Crear tipos de proyecto | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7bb4ac2f65180476bcc2a793c478c8900ae97cd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567238"
---
# <a name="creating-project-types"></a>Creación de tipos de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [crear tipos de proyecto](https://docs.microsoft.com/visualstudio/extensibility/internals/creating-project-types).  
  
Puede extender [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mediante la creación de un nuevo tipo de proyecto. Para crear un nuevo tipo de proyecto, debe comprender algunos conceptos y realizar una serie de pasos. Los temas siguientes proporcionan información general sobre cómo crear tipos de proyecto.  
  
## <a name="in-this-section"></a>En esta sección  
 [Decisiones de diseño del tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md)  
 Describe el elemento, persistencia de archivo de proyecto y las decisiones de diseño mecánico de compromiso que se deben realizar antes de crear un nuevo tipo de proyecto.  
  
 [Lista de comprobación: creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Proporciona información general de los pasos que debe seguir para crear un nuevo tipo de proyecto que admite tareas de programación como edición de código y compilar, compilar, depurar e implementar aplicaciones en el proyecto.  
  
 [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Proporciona información sobre cómo proporcionar y usar un generador de proyectos para crear instancias de un nuevo proyecto.  
  
 [Registro de un tipo de proyecto](../../extensibility/internals/registering-a-project-type.md)  
 Proporciona ejemplos de código de las instrucciones del registro que proporcionan rutas de acceso predeterminadas y datos y una tabla que contienen las entradas de la secuencia de comandos del registro para cada instrucción.  
  
 [Persistencia de un proyecto](../../extensibility/internals/project-persistence.md)  
 Describe el uso de `IPersistFileFormat` para conservar los archivos y objetos de proyectos no basados en archivos.  
  
 [Uso de MSBuild](../../extensibility/internals/using-msbuild.md)  
 Describe cómo puede usar el tipo de proyecto la [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] motor para permitir que los usuarios construido a partir de compilación [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y en la línea de comandos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Explica la arquitectura de código, herramientas de visualización, como el **Examinador de objetos** y **vista de clases** ventana. Describe las interfaces y métodos que se usan para implementar la búsqueda de objetos en un VSPackage.  
  
 [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Se explica el significado que se reproducen los proyectos en determinar qué editor se utiliza cuando se abre un elemento de proyecto y cómo se pueden manipular los recursos del proyecto.  
  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Muestra cómo proporcionar su propia identidad única a su VSPackage y cómo se ajustan los archivos DLL de VSPackage y otra información en un paquete de Windows Installer (. Archivo MSI) para la implementación a sus clientes.  
  
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Describe cómo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jerarquías de vistas y las direcciones.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Proporciona información general sobre un VSPackage, un objeto COM instalable que amplía el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno y se explica cómo implementar su propio paquete VSPackage.  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Describe cómo usar proyectos para modificar código, compilar y generar código y ejecutar y depurar el código y proporciona vínculos a temas detallados sobre cómo crear tipos de proyecto.

