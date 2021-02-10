---
title: Novedades &apos; de Visual Studio 2017 SDK | Microsoft Docs
description: El SDK de Visual Studio tiene características nuevas y actualizadas para Visual Studio 2017, incluido el formato actualizado de la versión 3 de VSIX.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9ab9183eacfc82aa70c22dec551883561b021b58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931254"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Novedades de&#39;s en el SDK de Visual Studio 2017

El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas para Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato VSIX V3

Para admitir la nueva instalación ligera de Visual Studio 2017, el formato de manifiesto de la extensión VSIX se ha actualizado a la versión 3 (VSIX V3).

El nuevo formato tiene compatibilidad con:

* Declarar explícitamente los requisitos previos que debe detectar e instalar el VSIXInstaller.
* Ensamblados Ngen en la instalación de la extensión.
* Instalación de recursos fuera de la raíz de la extensión habitual.

Para obtener información acerca de estos cambios, vea los temas siguientes:

* [Cambios en la extensibilidad de Visual Studio 2017](breaking-changes-2017.md)
* [Compatibilidad con Ngen en VSIX v3](ngen-support.md)
* [Instalar fuera de la carpeta de extensiones](set-install-root.md)
* [Preguntas más frecuentes sobre la extensibilidad de Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrar el proyecto de extensibilidad a Visual Studio 2017

Para obtener información sobre cómo actualizar los proyectos de extensibilidad y sus manifiestos de VSIX a Visual Studio 2017, vea [Cómo: migrar proyectos de extensibilidad a visual studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Plantillas de proyecto y de elemento personalizadas

A partir de Visual Studio 2017, ya no se comprobará si hay plantillas de proyecto y de elemento personalizadas. En su lugar, la extensión debe proporcionar archivos de manifiesto de plantilla que describan la ubicación de instalación de estas plantillas. Puede usar Visual Studio 2017 para actualizar las extensiones VSIX. Si implementa la extensión mediante un archivo MSI, debe generar los archivos de manifiesto de plantilla manualmente. Para obtener más información, vea [Actualizar plantillas de proyecto y de elemento personalizadas para Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). El esquema de manifiesto de plantilla se documenta en [Referencia de esquema de manifiesto de plantillas de Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Instrucciones de rendimiento de extensión actualizadas

Hay un nuevo artículo [Cómo: diagnosticar el rendimiento de la extensión](how-to-diagnose-extension-performance.md) en [administrar VSPackages](managing-vspackages.md) para mostrar cómo detectar y analizar el impacto de la extensión en los tiempos de inicio y carga de la solución de Visual Studio.
