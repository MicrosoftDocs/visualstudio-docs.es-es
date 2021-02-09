---
title: Ampliar proyectos | Microsoft Docs
description: Obtenga información sobre cómo crear sus propios tipos de proyecto personalizados en el SDK de Visual Studio y cómo administrar distintos tipos de soluciones de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 997f4e32007af641b24ba933d2c891e447382786
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895835"
---
# <a name="extend-projects"></a>Ampliar proyectos
Los proyectos y las soluciones son las formas en que Visual Studio organiza los archivos de código y de recursos en unidades de compilación e implementación. Puede encontrar más información sobre los proyectos en [proyectos (Visual Studio SDK)](../extensibility/extending-projects.md).

 Puede crear sus propios tipos de proyecto con el SDK de Visual Studio y Managed Package Framework para proyectos, que puede descargar en [Managed Package Framework for Projects](https://github.com/tunnelvisionlabs/MPFProj10). Para entender cómo se implementan los proyectos personalizados, vea [nueva generación de proyectos: debajo del capó, parte uno](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) y [nueva generación de proyectos: debajo del capó, parte dos](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 En los temas de esta sección se describe cómo crear proyectos personalizados y cómo administrar distintos tipos de soluciones de Visual Studio.

## <a name="in-this-section"></a>En esta sección
- [Crear un sistema de proyectos básico, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) Describe cómo crear un sistema de proyectos personalizado.

- [Creación de un sistema de proyectos básico, parte 2](../extensibility/creating-a-basic-project-system-part-2.md) Describe cómo crear un sistema de proyectos personalizado.

- [Guardar datos en archivos de proyecto](../extensibility/saving-data-in-project-files.md) Explica cómo agregar al proyecto (<em>.</em> proj *).

- [Comprobar los subtipos de un proyecto en tiempo de ejecución](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Explica cómo comprobar el subtipo de un proyecto en tiempo de ejecución.

- [Agregar y quitar páginas de propiedades](../extensibility/adding-and-removing-property-pages.md) Explica cómo personalizar las páginas de propiedades del proyecto personalizado.

- [Agregar un atributo a un elemento de proyecto](../extensibility/adding-an-attribute-to-a-project-item.md) Explica cómo agregar un atributo a un elemento de proyecto personalizado.

- [Conservar la propiedad de un elemento de proyecto](../extensibility/persisting-the-property-of-a-project-item.md) Explica cómo conservar las propiedades de un elemento de proyecto personalizado.

- [Administrar proyectos universales de Windows](../extensibility/managing-universal-windows-projects.md) Explica cómo administrar proyectos universales.
