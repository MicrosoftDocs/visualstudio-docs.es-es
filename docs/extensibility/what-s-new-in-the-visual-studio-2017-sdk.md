---
title: Lo&#39;s Nuevo en el SDK de Visual Studio 2017 Microsoft Docs
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88330aa68f2a3752431fd2fbe6c5c1c649acbb8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697208"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Qué&#39;s Nuevo en el SDK de Visual Studio 2017

El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas para Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato VSIX v3

Para admitir la nueva instalación ligera de Visual Studio 2017, el formato de manifiesto de extensión VSIX se ha actualizado a la versión 3 (VSIX v3).

El nuevo formato es compatible con:

* Declaración explícita de los requisitos previos que debe detectar e instalar VSIXInstaller.
* Ngen ensamblados en la instalación de la extensión.
* Instalación de activos fuera de la raíz de extensión habitual.

Para obtener más información sobre estos cambios, consulte los siguientes temas:

* [Cambios en la extensibilidad de Visual Studio 2017](breaking-changes-2017.md)
* [Compatibilidad con Ngen en VSIX v3](ngen-support.md)
* [Instalar fuera de la carpeta de extensiones](set-install-root.md)
* [Preguntas frecuentes sobre la extensibilidad de Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrar proyecto de extensibilidad a Visual Studio 2017

Para obtener información sobre cómo actualizar los proyectos de extensibilidad y sus manifiestos VSIX a Visual Studio 2017, vea Cómo: migrar proyectos de [extensibilidad a Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Plantillas personalizadas de proyectos y elementos

A partir de Visual Studio 2017, ya no se realizará el análisis de plantillas de proyecto y elemento personalizadas. En su lugar, la extensión debe proporcionar archivos de manifiesto de plantilla que describan la ubicación de instalación de estas plantillas. Puede usar Visual Studio 2017 para actualizar las extensiones VSIX. Si implementa la extensión mediante un MSI, debe generar los archivos de manifiesto de plantilla a mano. Para obtener más información, vea Actualizar plantillas de [proyecto y elemento personalizadas para Visual Studio 2017.](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md) El esquema de manifiesto de plantilla se documenta en la referencia de esquema de manifiesto de plantilla de [Visual Studio.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="updated-extension-performance-guidelines"></a>Directrices de rendimiento de la extensión actualizadas

Hay un nuevo artículo [Cómo: diagnosticar](how-to-diagnose-extension-performance.md) el rendimiento de la extensión en [Administrar VSPackages](managing-vspackages.md) para mostrar cómo detectar y analizar el impacto de la extensión en los tiempos de carga de la solución y el inicio de Visual Studio.
