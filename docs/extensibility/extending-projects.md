---
title: Extender proyectos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0333e09aee207e10657999dda4b5b1d59e181cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341108"
---
# <a name="extend-projects"></a>Extender proyectos
Proyectos y soluciones son las formas en que Visual Studio organiza los archivos de código y recursos en unidades de compilación e implementación. Puede encontrar más información sobre los proyectos en [proyectos (Visual Studio SDK)](../extensibility/extending-projects.md).

 Puede crear sus propios tipos de proyecto con el SDK de Visual Studio y Managed Package Framework para los proyectos, que puede descargarse en [Managed Package Framework for Projects](https://github.com/tunnelvisionlabs/MPFProj10). Para comprender cómo se implementan proyectos personalizados, vea [nueva generación de proyectos: Internamente, la primera parte](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) y [nueva generación de proyectos: Internamente, la segunda parte](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Los temas de esta sección describen cómo crear proyectos personalizados y cómo administrar distintos tipos de solución de Visual Studio.

## <a name="in-this-section"></a>En esta sección
- [Crear un sistema de proyectos básico, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) se describe cómo crear un sistema de proyecto personalizado.

- [Crear un sistema de proyectos básico, parte 2](../extensibility/creating-a-basic-project-system-part-2.md) se describe cómo crear un sistema de proyecto personalizado.

- [Guardar datos en archivos de proyecto](../extensibility/saving-data-in-project-files.md) Explains cómo agregar a proyecto (<em>.</em> archivos proj *).

- [Compruebe los subtipos de un proyecto en tiempo de ejecución](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) explica cómo comprobar el subtipo de un proyecto en tiempo de ejecución.

- [Agregar y quitar páginas de propiedades](../extensibility/adding-and-removing-property-pages.md) explica cómo personalizar las páginas de propiedades para el proyecto personalizado.

- [Agregar un atributo a un elemento de proyecto](../extensibility/adding-an-attribute-to-a-project-item.md) se explica cómo agregar un atributo a un elemento de proyecto personalizado.

- [Conservar la propiedad de un elemento de proyecto](../extensibility/persisting-the-property-of-a-project-item.md) explica cómo conservar las propiedades de un elemento de proyecto personalizado.

- [Administrar proyectos de Windows universales](../extensibility/managing-universal-windows-projects.md) se explica cómo administrar proyectos universales.