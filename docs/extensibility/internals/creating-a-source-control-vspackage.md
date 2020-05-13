---
title: Creación de un VSPackage de control de código fuente ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709192"
---
# <a name="create-a-source-control-vspackage"></a>Crear un control de código fuente VSPackage
Esta documentación incluye vínculos a la información general [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de la arquitectura de un paquete de control de código fuente integrado con , la API definida por las interfaces que se van a implementar y los servicios que se van a consumir, y un ejemplo que ilustra una implementación de paquete de control de código fuente simple.

 Con un control de código fuente VSPackage, puede crear [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]una ruta de acceso de integración profunda para que el control de código fuente se integre con . Permite que el paquete omita la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interfaz de usuario de control de código [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fuente predeterminada hospedada por , responda a las solicitudes de control de código fuente del sistema del proyecto e interactúe con componentes como el **Explorador**de soluciones . El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] permite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a los asociados con un mecanismo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para crear un VSPackage que se puede integrar con el uso de un modelo de servicio.

## <a name="in-this-section"></a>En esta sección
- [Introducción](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Describe el paquete de control de código fuente, que es una alternativa más [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]avanzada al complemento de control de código fuente para implementar características de control de código fuente en .

- [Architecture](../../extensibility/internals/source-control-vspackage-architecture.md)

 Presenta un diagrama y explica los componentes de un paquete de control de código fuente.

- [Características](../../extensibility/internals/source-control-vspackage-features.md)

 Describe las diversas características de un paquete de control de código fuente.

- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Describe la estructura del VSPackage que un paquete de control de código fuente debe implementar para una integración profunda.

## <a name="related-sections"></a>Secciones relacionadas
- [Crear un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Describe cómo crear un complemento de control de código fuente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que proporciona funcionalidad de control de código fuente en la interfaz de usuario (UI) del control de código fuente.

- [Control de código fuente](../../extensibility/internals/source-control.md)

 Describe las opciones para implementar el control [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de código fuente como una característica integrada de .
