---
title: Novedades en el SDK de Visual Studio 2017 | Documentos de Microsoft
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 3da360fc4df5516f5d976f807319c07b49d8c4e8
ms.lasthandoff: 03/07/2017

---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Novedades en el SDK de Visual Studio 2017

El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas de 2017 de Visual Studio.

## <a name="vsix-v3-format"></a>Formato VSIX v3

Para admitir la nueva instalación ligera de 2017 de Visual Studio, el formato de manifiesto de VSIX extensión se actualizó a la versión 3 (v3 VSIX).

El nuevo formato tiene compatibilidad para:

* La declaración explícita de los requisitos previos para detectar e instalado por el VSIXInstaller.
* Ensamblados de Ngen en la instalación de la extensión.
* Instalar recursos fuera de la raíz de extensión habitual.

Para obtener más información acerca de estos cambios, vea los temas siguientes:

* [Cambios a la extensibilidad de 2017](breaking-changes-2017.md)
* [Compatibilidad con Ngen en VSIX v3](ngen-support.md)
* [Instalación fuera de la carpeta de extensiones](set-install-root.md)
* [Preguntas más frecuentes para la extensibilidad de Visual Studio de 2017](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Migrar proyecto de extensibilidad de Visual Studio de 2017

Para obtener información sobre cómo actualizar los proyectos de extensibilidad y sus manifiestos VSIX a 2017 de Visual Studio, consulte [Cómo: migrar proyectos de extensibilidad en Visual Studio de 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="lightweight-solution-load-lsl"></a>Carga de la solución ligera (LSL)

Carga ligera de solución es una nueva característica de 2017 frente a lo que reducirá significativamente el tiempo de carga de la solución, lo que le permite ser más productivos más rápidamente. Cuando se habilita LSL, Visual Studio no totalmente cargar proyectos hasta que comience a trabajar con ellos.

LSL puede afectar a las extensiones de Visual Studio. Extensiones cuyas características dependen de un proyecto está totalmente cargado no funcionan o no funcionen correctamente. Consulte [ligero solución carga](lightweight-solution-load-extension-impact.md) para saber si la extensión puede verse afectado y obtener orientación sobre la actualización de la extensión.

## <a name="custom-project-and-item-templates"></a>Plantillas de proyecto y de elementos personalizadas

A partir de Visual Studio de 2017, análisis de proyecto personalizadas y plantillas de elementos ya no se realizará. En su lugar, la extensión debe proporcionar los archivos de manifiesto de plantilla que describen la ubicación de instalación de estas plantillas. Puede usar Visual Studio de 2017 para actualizar las extensiones VSIX. Si implementa la extensión de un archivo MSI, debe generar manualmente los archivos de manifiesto de la plantilla. Para obtener más información, consulte [Actualizar proyecto de personalizados y plantillas de elementos de Visual Studio de 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). El esquema de manifiesto de la plantilla se documenta en [Visual Studio Template manifiesto Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Instrucciones de rendimiento de la extensión actualizada

Hay una nueva [Cómo: diagnosticar rendimiento extensión](how-to-diagnose-extension-performance.md) tema en [administrar VSPackages](managing-vspackages.md) para mostrar cómo detectar y analizar el impacto de la extensión en Visual Studio inicio y solución de los tiempos de carga.

