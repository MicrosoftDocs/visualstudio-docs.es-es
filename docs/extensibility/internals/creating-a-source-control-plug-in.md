---
title: Crear un complemento de control de código fuente | Microsoft Docs
description: Obtenga información sobre cómo crear un complemento de control de código fuente que agregue una capacidad de control de código fuente al entorno de desarrollo integrado (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc302ee7327740380bb02e28c99e5117c926c7bc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056901"
---
# <a name="create-a-source-control-plug-in"></a>Crear un complemento de control de código fuente
El SDK de Visual Studio proporciona recursos que permiten agregar funcionalidad de control de código fuente al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE). Permite usar cualquier archivo DLL de complemento que cumpla con la API del complemento de control de código fuente que se describe en esta documentación.

## <a name="in-this-section"></a>En esta sección
- [Introducción](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Describe cómo instalar un complemento de control de código fuente y resalta las versiones de la API del complemento de control de código fuente disponibles actualmente.

- [Arquitectura](../../extensibility/internals/source-control-plug-in-architecture.md)

 Usa un diagrama de arquitectura para explicar la integración de un complemento de control de código fuente con el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Guía de pruebas](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Proporciona instrucciones sobre cómo probar la instalación y el funcionamiento de un complemento de control de código fuente.

## <a name="related-sections"></a>Secciones relacionadas
- [Crear un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Describe cómo crear un VSPackage de control de código fuente que no solo proporciona la funcionalidad de control de código fuente, sino que reemplaza la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario del control de código fuente.

- [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)

 Proporciona una lista completa de todos los elementos de la API del complemento de control de código fuente.

- [Control de código fuente](../../extensibility/internals/source-control.md)

 Describe las opciones para implementar el control de código fuente como una característica integrada de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
