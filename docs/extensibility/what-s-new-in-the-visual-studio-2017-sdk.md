---
title: Novedades &apos; del SDK de Visual Studio 2017 | Microsoft Docs
description: El SDK Visual Studio tiene características nuevas y actualizadas para Visual Studio 2017, incluido el formato VSIX versión 3 actualizado.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0b0b7852fa7e20f4ee6951e57c5c19f4b5454028
ms.sourcegitcommit: 3c6c263a1c0b20f084290ce45295a46027da33b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2021
ms.locfileid: "113756898"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Novedades&#39;del SDK de Visual Studio 2017

El SDK Visual Studio tiene las siguientes características nuevas y actualizadas para Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato VSIX v3

Para admitir la nueva instalación ligera de Visual Studio 2017, el formato de manifiesto de extensión VSIX se ha actualizado a la versión 3 (VSIX v3).

El nuevo formato es compatible con:

* Declarar explícitamente los requisitos previos que VSIXInstaller detectará e instalará.
* Ensamblados Ngen durante la instalación de la extensión.
* Instalación de recursos fuera de la raíz de extensión habitual.

Para obtener información sobre estos cambios, consulte los temas siguientes:

* [Cambios en la extensibilidad para Visual Studio 2017](breaking-changes-2017.md)
* [Compatibilidad con Ngen en VSIX v3](ngen-support.md)
* [Instalar fuera de la carpeta de extensiones](set-install-root.md)
* [Preguntas más frecuentes sobre la extensibilidad Visual Studio 2017](faq-2017.yml)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migración del proyecto de extensibilidad a Visual Studio 2017

Para obtener información sobre cómo actualizar los proyectos de extensibilidad y sus manifiestos VSIX a Visual Studio 2017, vea Migración de proyectos de [extensibilidad a Visual Studio 2017.](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

## <a name="custom-project-and-item-templates"></a>Plantillas personalizadas de proyecto y elemento

A partir de Visual Studio 2017, ya no se comprobará si hay plantillas de proyecto y de elemento personalizadas. En su lugar, la extensión debe proporcionar archivos de manifiesto de plantilla que describan la ubicación de instalación de estas plantillas. Puede usar Visual Studio 2017 para actualizar las extensiones VSIX. Si implementa la extensión mediante un archivo MSI, debe generar los archivos de manifiesto de plantilla manualmente. Para obtener más información, vea Actualizar plantillas personalizadas de proyecto [y elemento para Visual Studio 2017.](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md) El esquema de manifiesto de plantilla se documenta en [Referencia de esquema de manifiesto de plantillas de Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Directrices de rendimiento de extensión actualizadas

Hay un nuevo artículo How [to: Diagnose extension performance (Cómo:](how-to-diagnose-extension-performance.md) Diagnosticar el rendimiento de la extensión) en Manage VSPackages (Administrar [VSPackages)](managing-vspackages.md) para mostrar cómo detectar y analizar el impacto de la extensión en los tiempos de carga de Visual Studio inicio y solución.
