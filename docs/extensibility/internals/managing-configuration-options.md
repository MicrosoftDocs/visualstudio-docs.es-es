---
title: Administración de las opciones de configuración | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e093b3af6c0db75282d12f8766d36bc511d2cf4c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328651"
---
# <a name="managing-configuration-options"></a>Administración de opciones de configuración
Cuando se crea un nuevo tipo de proyecto, debe administrar opciones de configuración de soluciones y proyectos que determinan cómo el proyecto se compilará, empaquetadas, implementar y ejecutar. Los temas siguientes describen la configuración de soluciones y proyectos.

## <a name="in-this-section"></a>En esta sección
- [Información general](../../extensibility/internals/configuration-options-overview.md)

 Describe cómo los proyectos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] puede admitir varias configuraciones.

- [Páginas de propiedades](../../extensibility/internals/property-pages.md)

 Se explica que los usuarios pueden ver y cambiar las propiedades dependientes de la configuración de proyecto y propiedades independientes mediante el uso de páginas de propiedades.

- [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)

 Proporciona información sobre lo que se almacena en configuraciones de soluciones y cómo las configuraciones de soluciones dirigen el comportamiento de la **iniciar** y **compilar** comandos.

- [Objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md)

 Explica cómo el objeto de configuración de proyecto administra la presentación de información de configuración de la interfaz de usuario.

- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)

 Explica cómo se administra una lista de configuraciones de soluciones para una solución determinada por la **configuraciones de soluciones** cuadro de diálogo.

- [Configuración del proyecto para administrar la implementación](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 Define la acción de implementación y las dos maneras [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es compatible con proyectos que admiten la implementación.

- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)

 Explica los procesos de compilación que pueden admitir todas las configuraciones y las interfaces y métodos de salida de qué elementos pueden estar disponibles.

## <a name="related-sections"></a>Secciones relacionadas
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Proporciona información general de los proyectos como bloques de creación básicos de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE). Se proporcionan vínculos a temas adicionales que explican cómo proyectos de control de generar y compilar código.