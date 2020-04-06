---
title: Creación de un complemento de control de código fuente ( Source Control Plug-in) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e0d9dc54a61cabe7bdd5c21c10abf0def34ff6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709179"
---
# <a name="create-a-source-control-plug-in"></a>Crear un complemento de control de código fuente
El SDK de Visual Studio proporciona recursos que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le permiten agregar la capacidad de control de código fuente al entorno de desarrollo integrado (IDE). Le permite usar cualquier archivo DLL de complemento que cumpla con la API de complemento de Control de código fuente que se describe en esta documentación.

## <a name="in-this-section"></a>En esta sección
- [Introducción](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Describe cómo instalar un complemento de control de código fuente y resalta las versiones de API de complemento de Control de código fuente disponibles actualmente.

- [Architecture](../../extensibility/internals/source-control-plug-in-architecture.md)

 Utiliza un diagrama de arquitectura para explicar la integración de un complemento de control de código fuente con el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Guía de prueba](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Proporciona instrucciones sobre cómo probar la instalación y el funcionamiento de un complemento de control de código fuente.

## <a name="related-sections"></a>Secciones relacionadas
- [Crear un control de código fuente VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Describe cómo crear un control de código fuente VSPackage que no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solo proporciona funcionalidad de control de código fuente, sino que reemplaza la interfaz de usuario del control de código fuente.

- [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)

 Proporciona una lista completa de todos los elementos de la API de complemento de Control de código fuente.

- [Control de código fuente](../../extensibility/internals/source-control.md)

 Describe las opciones para implementar el control [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de código fuente como una característica integrada de .
