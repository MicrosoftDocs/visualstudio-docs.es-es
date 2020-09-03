---
title: Administrar opciones de configuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e18c308d74f8c20267c286c47d0e89bf82cd2850
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707308"
---
# <a name="managing-configuration-options"></a>Administración de opciones de configuración
Al crear un nuevo tipo de proyecto, debe administrar las opciones de configuración del proyecto y de la solución que determinan cómo se compilará, empaquetará, implementará y ejecutará el proyecto. En los temas siguientes se describe la configuración de proyectos y soluciones.

## <a name="in-this-section"></a>En esta sección
- [Información general](../../extensibility/internals/configuration-options-overview.md)

 Describe cómo los proyectos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pueden admitir varias configuraciones.

- [Páginas de propiedades](../../extensibility/internals/property-pages.md)

 Explica que los usuarios pueden ver y cambiar las propiedades dependientes de la configuración del proyecto y las propiedades independientes mediante páginas de propiedades.

- [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)

 Proporciona información sobre lo que se almacena en las configuraciones de soluciones y cómo las configuraciones de soluciones dirigen el comportamiento de los comandos **Start** y **Build** .

- [Objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md)

 Explica cómo el objeto de configuración de proyecto administra la presentación de la información de configuración en la interfaz de usuario.

- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)

 Explica cómo se administra una lista de configuraciones de soluciones para una solución determinada mediante el cuadro de diálogo **configuraciones de soluciones** .

- [Configuración del proyecto para administrar la implementación](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 Define el acto de la implementación y los dos métodos compatibles [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con los proyectos que admiten la implementación.

- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)

 Explica los procesos de compilación que cada configuración puede admitir y las interfaces y los métodos por los que los elementos de salida pueden estar disponibles.

## <a name="related-sections"></a>Secciones relacionadas
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Proporciona información general sobre los proyectos como los bloques de creación básicos del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE). Se proporcionan vínculos a temas adicionales que explican cómo los proyectos controlan la compilación y compilación de código.
