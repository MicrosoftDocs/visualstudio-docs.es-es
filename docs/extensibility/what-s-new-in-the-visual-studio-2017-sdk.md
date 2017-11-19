---
title: "¿Qué &#39; s nuevos en el SDK de Visual Studio de 2017 | Documentos de Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0be477d54ffeab52c415890c7d95447fa3f55ffc
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2017
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>¿Qué &#39; s nuevos en el SDK de Visual Studio de 2017

El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas de Visual Studio de 2017.

## <a name="vsix-v3-format"></a>Formato de v3 VSIX

Para admitir la nueva instalación ligera de 2017 de Visual Studio, el formato de manifiesto de VSIX extensión se ha actualizado a la versión 3 (v3 VSIX).

El nuevo formato tiene compatibilidad con:

* Declarar explícitamente los requisitos previos que se detecta y se instala mediante el VSIXInstaller.
* Ensamblados de Ngen a instalar la extensión.
* Instalar activos fuera de la raíz de la extensión habitual.

Para obtener información sobre estos cambios, vea los temas siguientes:

* [Cambios a la extensibilidad de 2017](breaking-changes-2017.md)
* [Compatibilidad con Ngen en VSIX v3](ngen-support.md)
* [Instalación fuera de la carpeta de extensiones](set-install-root.md)
* [Preguntas más frecuentes para la extensibilidad de Visual Studio de 2017](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Migrar proyectos de extensibilidad para Visual Studio de 2017

Para obtener información sobre cómo actualizar los proyectos de extensibilidad y sus manifiestos VSIX en Visual Studio de 2017, consulte [Cómo: migrar los proyectos de extensibilidad en Visual Studio de 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Plantillas de proyecto y de elementos personalizadas

A partir de Visual Studio de 2017, análisis de plantillas para proyectos y plantillas de elementos ya no se realizará. En su lugar, la extensión debe proporcionar los archivos de manifiesto de plantilla que describen la ubicación de instalación de estas plantillas. Puede usar Visual Studio de 2017 para actualizar las extensiones VSIX. Si implementa la extensión utilizando un archivo MSI, debe generar manualmente los archivos de manifiesto de la plantilla. Para obtener más información, consulte [actualizar un proyecto y plantillas de elementos de Visual Studio de 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). El esquema del manifiesto de plantilla se documenta en [referencia de esquema del manifiesto de Visual Studio plantilla](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Instrucciones de rendimiento de la extensión actualizada

Hay una nueva [Cómo: diagnosticar el rendimiento de la extensión](how-to-diagnose-extension-performance.md) tema en [administrar VSPackages](managing-vspackages.md) para mostrar cómo detectar y analizar el impacto de la extensión en Visual Studio inicio y solución de los tiempos de carga.
