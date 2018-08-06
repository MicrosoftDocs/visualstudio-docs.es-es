---
title: ¿Qué&#39;s en el SDK de Visual Studio 2017 | Microsoft Docs
ms.custom: ''
ms.date: 10/31/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f2a003bc19764aa07262552d3f0cc41316835b6
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566913"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>¿Qué&#39;s nuevo en Visual Studio 2017 SDK

El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas para Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato VSIX v3

Para admitir la nueva instalación ligera de Visual Studio 2017, el formato de manifiesto de extensión VSIX se actualizó a la versión 3 (v3 VSIX).

El nuevo formato es compatible con:

* Requisitos previos detecta e instalarse mediante el VSIXInstaller se declaran explícitamente.
* Ensamblados Ngen de instalación de la extensión.
* Instalación de los recursos fuera de la raíz de extensión habitual.

Para obtener información acerca de estos cambios, vea los temas siguientes:

* [Cambios a la extensibilidad de 2017](breaking-changes-2017.md)
* [Compatibilidad con Ngen en VSIX v3](ngen-support.md)
* [Instale fuera de la carpeta de extensiones](set-install-root.md)
* [Extensibilidad de Visual Studio 2017 preguntas más frecuentes](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrar el proyecto de extensibilidad a Visual Studio 2017

Para obtener información sobre cómo actualizar los proyectos de extensibilidad y sus manifiestos VSIX a Visual Studio 2017, consulte [Cómo: migrar proyectos de extensibilidad de Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Plantillas de proyecto y elemento personalizadas

A partir de Visual Studio 2017, análisis de proyecto personalizado y las plantillas de elemento ya no se realizará. En su lugar, la extensión debe proporcionar los archivos de manifiesto de plantilla que describen la ubicación de instalación de estas plantillas. Puede usar Visual Studio 2017 para actualizar las extensiones VSIX. Si implementa la extensión con un archivo MSI, debe generar manualmente los archivos de manifiesto de plantilla. Para obtener más información, consulte [actualizar plantillas de proyecto y elemento personalizadas para Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). El esquema del manifiesto de plantilla está documentado en [referencia de esquema del manifiesto de plantilla de Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Directrices de rendimiento de la extensión actualizada

Hay un nuevo [Cómo: diagnosticar el rendimiento de la extensión](how-to-diagnose-extension-performance.md) en el artículo [administrar VSPackages](managing-vspackages.md) para mostrar cómo detectar y analizar el impacto de la extensión en Visual Studio inicio y solución de los tiempos de carga.
