---
title: Crear un complemento de control de código fuente | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709179"
---
# <a name="create-a-source-control-plug-in"></a>Crear un complemento de control de código fuente
El SDK de Visual Studio proporciona recursos que permiten agregar funcionalidad de control de código fuente al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE). Permite usar cualquier archivo DLL de complemento que cumpla con la API del complemento de control de código fuente que se describe en esta documentación.

## <a name="in-this-section"></a>En esta sección
- [Introducción](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Describe cómo instalar un complemento de control de código fuente y resalta las versiones de la API del complemento de control de código fuente disponibles actualmente.

- [Architecture](../../extensibility/internals/source-control-plug-in-architecture.md)

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
