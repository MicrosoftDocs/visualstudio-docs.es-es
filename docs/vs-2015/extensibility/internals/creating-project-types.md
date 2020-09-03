---
title: Crear tipos de proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbe65d1615603e4dc7546dbfe3530093c62528e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155032"
---
# <a name="creating-project-types"></a>Creación de tipos de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Puede extender [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mediante la creación de un nuevo tipo de proyecto. Para crear un nuevo tipo de proyecto, debe comprender varios conceptos y completar una serie de pasos. En los temas siguientes se proporciona información general sobre cómo crear tipos de proyecto.  
  
## <a name="in-this-section"></a>En esta sección  
 [Decisiones de diseño del tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md)  
 Describe el elemento, la persistencia de los archivos de proyecto y las decisiones de diseño del mecánico de compromiso que debe realizar antes de crear un nuevo tipo de proyecto.  
  
 [Lista de comprobación: Creación de nuevos tipos de proyectos](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Proporciona información general sobre los pasos que debe seguir para crear un nuevo tipo de proyecto que admita tareas de programación como editar código y compilar, compilar, depurar e implementar aplicaciones en el proyecto.  
  
 [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Proporciona información sobre cómo proporcionar y utilizar un generador de proyectos para crear instancias de un nuevo proyecto.  
  
 [Registro de un tipo de proyecto](../../extensibility/internals/registering-a-project-type.md)  
 Proporciona ejemplos de código de instrucciones del registro que proporcionan las rutas de acceso y los datos predeterminados, y una tabla que contiene entradas del script del registro para cada instrucción.  
  
 [Persistencia de un proyecto](../../extensibility/internals/project-persistence.md)  
 Describe el uso de `IPersistFileFormat` para conservar objetos de proyecto de archivos y no basados en archivos.  
  
 [Usar MSBuild](../../extensibility/internals/using-msbuild.md)  
 Describe cómo el tipo de proyecto puede utilizar el [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] motor de compilación para permitir a los usuarios compilar desde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y hacia la línea de comandos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Explica la arquitectura de las herramientas de visualización de código como el **Examinador de objetos** y la ventana de **vista de clases** . Describe las interfaces y los métodos que se usan para implementar la exploración de objetos en un VSPackage.  
  
 [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Describe la importancia de los proyectos a la hora de determinar qué editor se usa cuando se abre un elemento de proyecto y cómo se pueden manipular los recursos del proyecto.  
  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Muestra cómo proporcionar a su VSPackage su propia identidad única y cómo ajustar los archivos dll de VSPackage y otra información en un paquete de Windows Installer (. Archivo MSI) para la implementación en sus clientes.  
  
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Describe cómo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] las vistas y dirigen a las jerarquías.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Proporciona información general de un VSPackage, un objeto COM instalable que extiende el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno y describe cómo implementar su propio VSPackage.  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Describe cómo usar proyectos para modificar código, compilar y compilar código, y ejecutar y depurar código, y proporciona vínculos a temas detallados sobre cómo crear tipos de proyecto.
