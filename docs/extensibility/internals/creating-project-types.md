---
title: Creación de tipos de proyecto ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709066"
---
# <a name="create-project-types"></a>Crear tipos de proyecto
Puede ampliar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creando un nuevo tipo de proyecto. Para crear un nuevo tipo de proyecto, debe comprender varios conceptos y completar una serie de pasos. Los temas siguientes proporcionan información general sobre cómo crear tipos de proyecto.

## <a name="in-this-section"></a>En esta sección
- [Decisiones de diseño de tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md)

 Describe las decisiones de diseño de mecánica de elementos, persistencia de archivos de proyecto y compromiso que debe tomar antes de crear un nuevo tipo de proyecto.

- [Lista de verificación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)

 Proporciona información general sobre los pasos que debe seguir para crear un nuevo tipo de proyecto que admita tareas de programación como editar código y compilar, compilar, depurar e implementar aplicaciones en el proyecto.

- [Crear instancias de proyecto mediante fábricas de proyectos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Proporciona información sobre cómo proporcionar y usar un generador de proyectos para crear instancias de un nuevo proyecto.

- [Registrar un tipo de proyecto](../../extensibility/internals/registering-a-project-type.md)

 Proporciona ejemplos de código de instrucciones del registro que proporcionan rutas de acceso y datos predeterminados, y una tabla que contiene entradas del script del Registro para cada instrucción.

- [Persistencia del proyecto](../../extensibility/internals/project-persistence.md)

 Describe el uso `IPersistFileFormat` de conservar objetos de proyecto no basados en archivos y no basados en archivos.

- [Usar MSBuild](../../extensibility/internals/using-msbuild.md)

 Describe cómo el tipo de [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] proyecto puede usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el motor de compilación para permitir que los usuarios se compilen desde y en la línea de comandos.

## <a name="related-sections"></a>Secciones relacionadas
- [Soporta herramientas de navegación de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Explica la arquitectura de herramientas de visualización de código como el **Examinador de objetos** y la ventana Vista de **clases.** Describe las interfaces y métodos que se usan para implementar la exploración de objetos en un VSPackage.

- [Agregar plantillas de proyecto y elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Describe la importancia que juegan los proyectos para determinar qué editor se utiliza cuando se abre un elemento de proyecto y cómo se pueden manipular los recursos del proyecto.

- [Instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Muestra cómo dar al VSPackage su propia identidad única y cómo ajustar los archivos DLL de VSPackage y otra información en un paquete de Windows Installer (*. MSI)* para su implementación a sus clientes.

- [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Describe cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se describen las vistas y las jerarquías.

- [VSPackages](../../extensibility/internals/vspackages.md)

 Proporciona información general de un VSPackage, un objeto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] COM instalable que extiende el entorno y describe cómo implementar su propio VSPackage.

- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Describe cómo usar proyectos para modificar código, compilar y compilar código y ejecutar y depurar código, y proporciona vínculos a temas detallados sobre cómo crear tipos de proyecto.
