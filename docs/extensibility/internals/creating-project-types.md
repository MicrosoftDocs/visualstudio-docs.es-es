---
title: Crear tipos de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2398b63b8cd52784252cfc764bb6c6a30e1accc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709066"
---
# <a name="create-project-types"></a>Crear tipos de proyecto
Puede extender [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante la creación de un nuevo tipo de proyecto. Para crear un nuevo tipo de proyecto, debe comprender varios conceptos y completar una serie de pasos. En los temas siguientes se proporciona información general sobre cómo crear tipos de proyecto.

## <a name="in-this-section"></a>En esta sección
- [Decisiones de diseño de tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md)

 Describe el elemento, la persistencia de los archivos de proyecto y las decisiones de diseño del mecánico de compromiso que debe realizar antes de crear un nuevo tipo de proyecto.

- [Lista de comprobación: crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)

 Proporciona información general sobre los pasos que debe seguir para crear un nuevo tipo de proyecto que admita estas tareas de programación como editar código y compilar, compilar, depurar e implementar aplicaciones en el proyecto.

- [Creación de instancias de proyecto mediante el uso de generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Proporciona información sobre cómo proporcionar y utilizar un generador de proyectos para crear instancias de un nuevo proyecto.

- [Registrar un tipo de proyecto](../../extensibility/internals/registering-a-project-type.md)

 Proporciona ejemplos de código de instrucciones del registro que proporcionan las rutas de acceso y los datos predeterminados, y una tabla que contiene entradas del script del registro para cada instrucción.

- [Persistencia del proyecto](../../extensibility/internals/project-persistence.md)

 Describe el uso de `IPersistFileFormat` para conservar objetos de proyecto de archivos y no basados en archivos.

- [Usar MSBuild](../../extensibility/internals/using-msbuild.md)

 Describe cómo el tipo de proyecto puede utilizar el [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] motor de compilación para permitir a los usuarios compilar desde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y hacia la línea de comandos.

## <a name="related-sections"></a>Secciones relacionadas
- [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Explica la arquitectura de las herramientas de visualización de código como el **Examinador de objetos** y la ventana de **vista de clases** . Describe las interfaces y los métodos que se usan para implementar la exploración de objetos en un VSPackage.

- [Agregar plantillas de proyecto y de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Describe la importancia de los proyectos a la hora de determinar qué editor se usa cuando se abre un elemento de proyecto y cómo se pueden manipular los recursos del proyecto.

- [Instale VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Muestra cómo proporcionar a su VSPackage su propia identidad única y cómo ajustar los archivos dll de VSPackage y otra información en un paquete de Windows Installer (*. Archivo MSI* ) para la implementación en sus clientes.

- [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Describe cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las vistas y dirigen a las jerarquías.

- [VSPackages](../../extensibility/internals/vspackages.md)

 Proporciona información general de un VSPackage, un objeto COM instalable que extiende el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno y describe cómo implementar su propio VSPackage.

- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Describe cómo usar proyectos para modificar código, compilar y compilar código, y ejecutar y depurar código, y proporciona vínculos a temas detallados sobre cómo crear tipos de proyecto.
