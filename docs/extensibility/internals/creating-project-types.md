---
title: Crear tipos de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa58b0195c0fbcf50cce0ac5300ab142c4de93d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="creating-project-types"></a>Crear tipos de proyecto
Puede extender [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante la creación de un nuevo tipo de proyecto. Para crear un nuevo tipo de proyecto, debe entender algunos conceptos y realizar una serie de pasos. Los temas siguientes proporcionan información general sobre cómo crear tipos de proyecto.  
  
## <a name="in-this-section"></a>En esta sección  
 [Decisiones de diseño del tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md)  
 Describe el elemento, persistencia de archivo de proyecto y las decisiones de diseño mecánico de compromiso que se deben realizar antes de crear un nuevo tipo de proyecto.  
  
 [Lista de comprobación: creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Proporciona información general de los pasos que debe seguir para crear un nuevo tipo de proyecto que es compatible con las tareas de programación como edición de código y compilar, compilación, depuración e implementación de aplicaciones en el proyecto.  
  
 [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Proporciona información sobre cómo proporcionar y utilizar un generador de proyecto para crear instancias de un nuevo proyecto.  
  
 [Registro de un tipo de proyecto](../../extensibility/internals/registering-a-project-type.md)  
 Proporciona ejemplos de código de las instrucciones del registro que proporcionan rutas de acceso predeterminadas y los datos y una tabla que contienen las entradas de la secuencia de comandos del registro para cada instrucción.  
  
 [Persistencia de un proyecto](../../extensibility/internals/project-persistence.md)  
 Describe el uso de `IPersistFileFormat` para conservar los archivos y objetos del proyecto no basados en archivos.  
  
 [Uso de MSBuild](../../extensibility/internals/using-msbuild.md)  
 Describe cómo puede utilizar el tipo de proyecto la [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] motor para permitir que los usuarios se crean a partir de compilación [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y en la línea de comandos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Explica la arquitectura del código herramientas de visualización, como el **Examinador de objetos** y **vista de clases** ventana. Describe las interfaces y métodos que se usan para implementar la exploración de objetos en un paquete VSPackage.  
  
 [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Se explica el significado que se reproducen proyectos para determinar qué editor se utiliza cuando se abre un elemento de proyecto y cómo se pueden manipular los recursos del proyecto.  
  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Muestra cómo proporcionar el VSPackage su propia identidad única y cómo ajustar los archivos DLL de VSPackage y otra información en un paquete de Windows Installer (. Archivo MSI) para su implementación en los clientes.  
  
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Describe cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las jerarquías de vistas y las direcciones.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Proporciona información general de un VSPackage, un objeto COM instalable que extiende el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno y se explica cómo implementar su propia VSPackage.  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Describe cómo usar proyectos para modificar el código, compilar y generar código y ejecutar y depurar el código y proporciona vínculos a temas detallados sobre cómo crear tipos de proyecto.